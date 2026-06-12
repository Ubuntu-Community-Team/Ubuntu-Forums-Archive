---
title: "Authenicate PPA timed out"
date: 2009-10-16
forum: General Help
---

### Post by ShizzlePDX503 on 2009-10-16
I am trying to authenticate a key for a ppa that I added to my software sources. I am trying to install the current version of Banshee which is 1.5 this is the error that I get:

```
shizzle@shizzle-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
gpg: requesting key 6E80C6B7 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```do I just need to try later to see if it will work? I have tried a couple of times already but get the same result. I downloaded the tarball from banshee's website but their wiki is down so I am not sure how to compile it from the tarball.

I usually am able to add ppa sources this way:
```
shizzle@shizzle-laptop:~$ sudo add-apt-repository ppa:banshee-team/ppa

```but I get this error:
```
sudo: add-apt-repository: command not found
```any ideas as to why I get this error now?

---

### Post by ShizzlePDX503 on 2009-10-16
its working now... it isn't timing out any more

---

