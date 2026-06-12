---
title: "Automated ProFTPd Install"
date: 2009-12-27
forum: General Help
---

### Post by webmasteroy on 2009-12-27
Hello,

So I have a BASH script that automates the installation of many services, including ProFTPd...  Currently it is installing ProFTPd via, debian's package manager (apt-get), so I am running a command similiar to:

```
apt-get -y -q install proftpd
``` 

Unfortunately, doing this causes ProFTPd to prompt me (or the end-user) to choose a method to run ProFTPd as, "from inetd, standalone, etc.."  see this image.

I ran into the same problem with MySQL, it was asking for a root password... I was lucky enough to find a thread online, that someone had solved this problem he used a couple lines in his BASH script (that I believe, set values to by-pass the prompt) the code he used is as follows...

```

echo "mysql-server mysql-server/root_password select (password omitted)" | debconf-set-selections
echo "mysql-server mysql-server/root_password_again select (password omitted)" | debconf-set-selections
apt-get -y -q install mysql-server

```

I am wondering if there is a similiar procedure to automate or remove the prompt from the ProFTPd prompt...

Any help is greatly appreciated  :)

---

### Post by cariboo on 2009-12-27
If you're setting up servers that often that you want to automate the process, have a look at debootstrap, it will allow you to script the whole installation.

If you are just installing mysql with out entering a password for root, I sure hope you aren't doing it on an outward facing server, as you are opening your self up to a whole lot of extra work when the server gets cracked.

There should be enough info on [this]("http://www.debian-administration.org/articles/383") page to allow you to script the installation of proftpd.

---

