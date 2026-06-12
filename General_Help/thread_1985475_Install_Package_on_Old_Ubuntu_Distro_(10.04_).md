---
title: "Install Package on Old Ubuntu Distro (10.04 )"
date: 2012-05-23
forum: General Help
---

### Post by hthakar on 2012-05-23
Dear All,

I have an old Ubuntu distro (10.04) on one machine which I had used in 2009 - 10. I want to install mysql-server on that machine but "sudo apt-get install" doesnt work as this distribution is not supported. 

What do I do?

Thanks.
Harsh.

---

### Post by sudodus on 2012-05-23
Ubuntu distro (10.04) is an LTS release with support until  April 2013. I'm running it right now, and received security updates today :-)

Furthermore, the corresponding server edition will be supported until April 2015. But it is only for server specific software. See the following thread
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1954702_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1954702")

So I think you have some other problem. Have you tried to run the following commands (and watch for error messages) before running the install command?
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by hthakar on 2012-05-24
It gives Err : *Server_Name* *PackageName* 404 Not found.

Am I using the wrong server? I went to synaptic package manager and selected various servers including the main server and server for India but no luck.

Harsh.

---

### Post by sudodus on 2012-05-24
Would it be an alternative for you to wipe the current OS and install a new one, for example Ubuntu server? Then you should have no issues with the packages.

---

