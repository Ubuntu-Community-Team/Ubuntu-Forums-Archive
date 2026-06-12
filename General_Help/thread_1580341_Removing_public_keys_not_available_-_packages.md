---
title: "Removing public keys not available - packages"
date: 2010-09-23
forum: General Help
---

### Post by kabeza on 2010-09-23
Hi 
I'm getting some errors while trying to do an update:

[[IMG]http://img814.imageshack.us/img814/3762/screenshot012ep.th.jpg[/IMG]](http://img814.imageshack.us/i/screenshot012ep.jpg/)

How can I know which are the apps that are causing this, and how should I remove/update these?

This is my /etc/apt/sources.list

```
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://linux.dropbox.com/ubuntu lucid main
deb-src http://linux.dropbox.com/ubuntu lucid main
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb http://ppa.launchpad.net/synce/ubuntu lucid main
deb http://ppa.launchpad.net/sugree/ubuntu lucid main
deb http://archive.canonical.com/ lucid partner
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
```

---

### Post by andrewthomas on 2010-09-23
> **kabeza said:**
> 

How can I know which are the apps that are causing this, and how should I remove/update these?

This is my /etc/apt/sources.list

```
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://linux.dropbox.com/ubuntu lucid main
deb-src http://linux.dropbox.com/ubuntu lucid main
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe multiverse
deb http://ppa.launchpad.net/synce/ubuntu lucid main
deb http://ppa.launchpad.net/sugree/ubuntu lucid main
deb http://archive.canonical.com/ lucid partner
# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
```
```
gksu gedit /etc/apt/sources.list
```then get rid of 

```
deb http://ppa.launchpad.net/synce/ubuntu lucid main
deb http://ppa.launchpad.net/sugree/ubuntu lucid main
```You have the wrong info for both ppa's 

**For the synce ppa**: you either need to 

```
sudo add-apt-repository ppa:synce/ppa
```which will add 

```
deb http://ppa.launchpad.net/synce/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/synce/ppa/ubuntu lucid main
``` and the key 

or ```
sudo add-apt-repository ppa:synce/synce-head
```which will add
```
deb http://ppa.launchpad.net/synce/synce-head/ubuntu lucid main 
deb-src http://ppa.launchpad.net/synce/synce-head/ubuntu lucid main
```and the key.

**As far as sugree**: you will get an error, since there is no repo for lucid, only jaunty, intrepid and hardy 
As you can see here:
[https://launchpad.net/~sugree/+archive/ppa]("https://launchpad.net/%7Esugree/+archive/ppa")

---

### Post by kabeza on 2010-09-24
Great Andrew!
Thanks for the help. You know, I had to add manually the addresses to sources.list because I'm having some problem:

[COLOR="Blue"]kike@kikeubuntu:~$ sudo add-apt-repository ppa:synce/ppa
[sudo] password for kike: 
Error reading [https://launchpad.net/api/1.0/~synce/+archive/ppa:](https://launchpad.net/api/1.0/~synce/+archive/ppa:) <urlopen error [Errno 113] No hay ruta hacia el host>
[/COLOR]
I've set a proxy in preferences, but it seems it doesn't work in terminal, maybe because it tries to get HTTPS

But the weird stuff is that I can browse the corresponding url in firefox
[https://launchpad.net/api/1.0/~synce/+archive/ppa](https://launchpad.net/api/1.0/~synce/+archive/ppa)

Do you know how could I fix this?
Thanks again

---

### Post by andrewthomas on 2010-09-24
This might help.

[http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-](http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-)

---

### Post by kabeza on 2010-09-27
Thanks andrew.
Did that bashrc thing before I read your post, but no luck

The strange problem about this is:

```
- I can do from terminal: sudo apt-get update
- I can do from terminal: sudo apt-get upgrade
- I can do from terminal: sudo apt-get install packageXXX
```

The only command that is giving me trouble is
```

sudo add-apt-repository XXX
```

---

