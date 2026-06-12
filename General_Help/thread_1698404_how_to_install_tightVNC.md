---
title: "how to install tightVNC"
date: 2011-03-02
forum: General Help
---

### Post by harkumar on 2011-03-02
hello, everybody.

I am using Ubuntu 10.10 netbook edition. 

I have already downloaded the ***tightvnc-1.3.10_unixsrc.tar.bz2*** , the source code for VNC. But I dont know how to install it. plz tell me the basic steps.

---

### Post by apemax on 2011-03-02
Hi harkumar.:)

Have a look here:

[http://www.tightvnc.com/docs.php]("http://www.tightvnc.com/docs.php")

Under the "Unix Version" section there's a link to the readme called "Unix Installation Help". have a look at that and see if it helps.

---

### Post by anglican on 2011-03-02
> **harkumar said:**
> hello, everybody.

I am using Ubuntu 10.10 netbook edition. 

I have already downloaded the ***tightvnc-1.3.10_unixsrc.tar.bz2*** , the source code for VNC. But I dont know how to install it. plz tell me the basic steps.But unless you have a **very** good reason to install from source, don't. Tightvnc is in the standard repos so you can install it with:
```
sudo apt-get install tightvncserver
```which will let the package management know about it making uninstalling and updating much simpler.

H

---

### Post by harkumar on 2011-03-02
> **anglican said:**
> But unless you have a **very** good reason to install from source, don't. Tightvnc is in the standard repos so you can install it with:
```
sudo apt-get install tightvncserver
```which will let the package management know about it making uninstalling and updating much simpler.

H
have installed. plz tell me how to configure and run it.
How to use the ***tightvncviwer***??
Is it automatically installed with **tightvncserver**??

---

### Post by YesWeCan on 2011-03-02
To run tightvncserver on the server 'vncserver'
It will ask you for a client (viewer) access password.

On the client, just use Vinagre. I think it comes pre-installed in Applications/Accessories. If not, install from the software centre.

Tightvnc server will create an independent desktop on port 5901. If you run vncserver again it will make another at 5902, and so on. Your actual desktop on the server is at 5900. You don't use Tightvncserver to view this one.
Note that it is necessary for a user to be logged on to the server in order for Vinagre to be able to view a desktop instance of that user. The user can be logged in at the server or via ssh.

---

### Post by anglican on 2011-03-02
> **harkumar said:**
> have installed. plz tell me how to configure and run it.
How to use the ***tightvncviwer***??
Is it automatically installed with **tightvncserver**??Tightvncviewer is installed with the package xtightvncviewer. For how to use it, you need to say what you are hoping to achieve with tightvnc - it can be used in many ways and different situations.

H

---

### Post by harkumar on 2011-03-03
was hopping to connect a windows based PC using my Ubuntu based netbook.
Its done.
Thanks for the help.

---

