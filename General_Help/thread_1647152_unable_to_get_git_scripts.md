---
title: "unable to get git scripts"
date: 2010-12-16
forum: General Help
---

### Post by faixan on 2010-12-16
i'm having trouble installing the compiz experimental addons... i've proxy server which isn't allowing me to get the script through terminal
this is how it goes...

@ubuntu:~/Downloads$ git clone git://anongit.compiz.org/users/soreau/scripts
Initialized empty Git repository in /home/maverick/Downloads/scripts/.git/
fatal: Unable to look up anongit.compiz.org (port 9418) (Name or service not known)

is there any other way i can do this?
i've same trouble with adding PPA, used the software sources to make it work...

---

### Post by Gnomepocalypse on 2010-12-16
Hi faixan,

I'd take a look at [http://ubuntuforums.org/showthread.php?t=1575]("http://ubuntuforums.org/showthread.php?t=1575"), which goes over how to set your http_proxy environment variable. Also, [http://stackoverflow.com/questions/128035/how-do-i-pull-from-a-git-repository-through-an-http-proxy]("http://stackoverflow.com/questions/128035/how-do-i-pull-from-a-git-repository-through-an-http-proxy").

tl;dr:

```
Proxy support for apt-get package management

Define the http_proxy variable in the format [http://host:port/](http://host:port/). 
If you have to login then use the format [http://username:password@host:port/](http://username:password@host:port/). 
To define this variable add the following lines to the root login file /root/.bashrc.

http_proxy=http://username:password@host:port/
export http_proxy
```

```
You can also set the HTTP proxy that Git uses in global configuration property http.proxy:

git config --global http.proxy $http_proxy
```

---

### Post by faixan on 2010-12-16
> **Gnomepocalypse said:**
> Hi faixan,

I'd take a look at [http://ubuntuforums.org/showthread.php?t=1575]("http://ubuntuforums.org/showthread.php?t=1575"), which goes over how to set your http_proxy environment variable. Also, [http://stackoverflow.com/questions/128035/how-do-i-pull-from-a-git-repository-through-an-http-proxy]("http://stackoverflow.com/questions/128035/how-do-i-pull-from-a-git-repository-through-an-http-proxy").

tl;dr:

```
Proxy support for apt-get package management

Define the http_proxy variable in the format [http://host:port/](http://host:port/). 
If you have to login then use the format [http://username:password@host:port/](http://username:password@host:port/). 
To define this variable add the following lines to the root login file /root/.bashrc.

http_proxy=http://username:password@host:port/
export http_proxy
```

```
You can also set the HTTP proxy that Git uses in global configuration property http.proxy:

git config --global http.proxy $http_proxy
```


i'm familiar with the proxy setup, it's just the specific port for git seems to be blocked at the proxy server... :(
i wanted to know if there was any other way to do all what the above command does, without using the git protocol?

---

