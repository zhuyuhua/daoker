你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
# Daoker
Daoker is a tool to manage Docker environment regardless of docker daemon's failure.

Docker is an open source project to build, ship and run any application as a 
lightweight container. If you have some experience in operating Docker in developing,
testing or production environment, you will find that the architecture of Docker is
composed of **four parts: Docker CLI, Docker Daemon, Docker Images and Docker Container**.

## Background
I believe that Docker is totally production-ready, while we still run into some cases
that Docker Daemon does not work as we wish, such as :

* command `docker ps` hangs
* command `docker inspect` hangs
* no details about docker environment, no right to talk about management
* and so on

If situations above happen to you, we can judge that you lose the control of docker.
If it is your developing environment, you can change a machine with Docker to avoid
some problems. And if it is production environment, I think everyone should realized
the gravity of this situation.

## Principles
As Docker Daemon fails, we have no idea about whether docker api is working which
seems so disappointing. **Disappointing, but not fatal**.

Have you ever experienced that Docker Daemon stores almost all details about Docker
Container in its local filesystem? If the answer is "Yes", you've got what I am
going to do.

Following is two most important principles:

* **NEVER** to contact with docker daemon
* take advantage of **DOCKER_ROOT** and **CGROUP FILESYSTEM** to do everything you want

## Get Started

Daoker is CLI tool to handle tough things when docker daemon fails. We had better read
`daoker help` to get more instruments.

```
root@daocloud:~/daoker# daoker help
NAME:
   daoker - A tool to manage Docker environment when Docker fails

USAGE:
   daoker [global options] command [command options] [arguments...]

VERSION:
   0.0.1

AUTHOR(S):
   Allen Sun <allen.sun@daocloud.io>

COMMANDS:
    ps		List containers
    kill	Stop a container forcefully
    stop	Stop a container
    volume	Show all details of a container's volumes
    pid		Print container name if it contains the given pid
    oom		Return true if a container is under oom
    pidnum	Print process numbers in your specified container

GLOBAL OPTIONS:
   --debug			debug mode [$DEBUG]
   --log-level, -l "info"	Log level (options: debug, info, warn, error, fatal, panic)
   --help, -h			show help
   --version, -v		print the version
```

Then enjoy your jouney with daoker if you happen to find some commands are helpful to you.


## Build and Install Daoker
Before you **Build** and **Install** daoker, you should know some prerequisition:

* Linux only
* Ubuntu preferred
* Golang 1.5+ preferred
* Docker 1.10.0+ tested, lower version will be tested soon

```
git clone https://github.com/allencloud/daoker.git
cd daoker
export GOPATH=`pwd`
go get -d
go build -o daoker

mv daoker /usr/local/bin

```

Now `daoker` is in your PATH.

## Participating

You can contribute to Daoker in several different ways:

* To report a problem or request a feature, please feel free to file an issue.

* Of course, we welcome pull requests and patches. Setting up a local Daoker development environment and submitting PRs is described here.


## Copyright and license
Copyright © 2016. All rights reserved


