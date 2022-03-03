# Jenkins

Integração contínua no ciclo de desenvolvimento de um sistema.

## Princípio de IaC com o Jenkins

Divisão das tarefasÇ
- O desenvolvedor faz a tarefa criativa (o código);
- Jenkins faz as tarefas repetitivas (testes, deploy etc.). 

Obs.: Como tudo ta automatizado, podemos ter um sistema atualizado diversas vezes no mesmo dia.

Com o Jenkins é possível automatizar uma série de procedimentos, como:
- Deploy em um servidor;
- Rodar um conjunto de testes;
- Rodar scripts em um Banco de Dados;
- Atualizar uma aplicação web;
- Delegar a execução para outros servidores (slave).

## Instalação via Docker

### Install Docker

```
sudo curl -fsSL https://get.docker.com | bash
sudo usermod -aG docker $USER
```

### Instalando o Jenkins

Baixando versão LTS:

```bash
docker pull jenkins/jenkins:lts-jdk11
```

Comando de instalação:

```bash
docker run -p 8080:8080 jenkins
#Rodando com a configuração da porta extra e o volume
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11
```

Para saber mais:

- [Official Jenkins Docker image
](https://github.com/jenkinsci/docker/blob/master/README.md)


### Configuração inicial


Ver senha de admin em:

```bash
/var/jenkins_home/secrets/initialAdminPassword
```

Veja o nome do volume do Jenkins:


```bash
docker volume ls
```

Faça um inspect no volume:


```bash
docker volume inspect jenkins_home
```

## Banco de Dados

O Jenkins não utiliza banco de dados, ele grava todas as informações em disco, no diretório conhecido como JENKINS_HOME - que pode ser <DIRETÓRIO-HOME>/.jenkins ou /var/lib/jenkins em algumas distribuições Linux. Portanto, pensando em beckup, esse serã o diretório que devemos ter cópia.