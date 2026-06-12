---
title: "How to install softwares in custom location"
date: 2011-01-23
forum: General Help
---

### Post by snimavat on 2011-01-23
Hello,

I want to install additional softwares that I download to a custom location (other then what comes from ubuntu upgrade). 

1. How can I change the installation directory when installing packages
2. I want to keep my ubuntu installation clean and not mixed up with softwares i install, where should I be installing softwares, /home/softwares or /opt or some where else ?

I am the only user of the system

pl help.

---

### Post by endotherm on 2011-01-23
it depends on how stand-alone the program is I suppose, but you can execute a program you download from any location where you have the rights to do so. I have a folder called ~/sbin for my personal scripts, and I put global ones in /usr/sbin/. 

I have no idea if you can configure apt to do it for you though. I would probably only do this for stuff you write, compile, or download off the Internet, that you cant get from the repos, since you wouldn't get updates, and it may mess with the dist-upgrade options.

---

### Post by snimavat on 2011-01-23
> **endotherm said:**
> I would probably only do this for stuff you write, compile, or download off the Internet, that you cant get from the repos, since you wouldn't get updates, and it may mess with the dist-upgrade options.

Exactly, thats what I want to do, but when installing a package downloaded from internet, how do I specify where it should be installed? Lets say I want to install pidgin to a custom location /home/programs How do I do that?
I have downloaded the package from pidgin site.

---

### Post by endotherm on 2011-01-24
well all you can really do is call dpkg manually for your .deb package.


here is the manpage for dpkg 
[http://manpages.debian.net/cgi-bin/man.cgi?query=dpkg&apropos=0&sektion=0&manpath=Debian+Sid&format=html&locale=en](http://manpages.debian.net/cgi-bin/man.cgi?query=dpkg&apropos=0&sektion=0&manpath=Debian+Sid&format=html&locale=en)

check out the '--instdir=<dir>' option.

---

