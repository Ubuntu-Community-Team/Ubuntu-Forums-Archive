---
title: "Can't apt-get update :("
date: 2012-09-13
forum: General Help
---

### Post by devkurniadi on 2012-09-13
when i write apt-get update, the terminal show me this error.

> 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Please help, what should i do??

---

### Post by josephmills on 2012-09-13
Is synaptic package manager open Or another program that would be using apt ?
**EDIT**
also can we see a 
```
sudo lsof | grep /var/lib/dpkg/lock
```
what is locking it ?

---

### Post by grash on 2012-09-13
Try "sudo apt-get update" without the quotes.

---

### Post by devkurniadi on 2012-09-13
still show this error

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by devkurniadi on 2012-09-13
josephmills :

where is synaptic package manager?
sorry i'm new in ubuntu

---

### Post by josephmills on 2012-09-13
> 
That error message means that you aren't allowed to use two programs that use /var/lib/dpkg/lock 
dpkg is used to unpack software packages to be installed in your system some applications that use dpkg are: synaptic, ubuntu software center (when installing an application), apt-get, update manager and some others.




source
[http://askubuntu.com/questions/64997/error-message-e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-tempo](http://askubuntu.com/questions/64997/error-message-e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-tempo)

---

### Post by josephmills on 2012-09-13
> **devkurniadi said:**
> josephmills :

where is synaptic package manager?
sorry i'm new in ubuntu


cool please open up your terminal (ctrl+alt+t)
then enter in 

```
sudo lsof | grep /var/lib/dpkg/lock
```

then paste that here for us to see :) this will tell us what is locking it.

---

### Post by jerrrys on 2012-09-13
Do you have another package manager open while trying to use apt-get (like maybe the software center)?  You can have only one open at a time.

---

### Post by grash on 2012-09-13
You get the same error message as well if you're not root.

---

### Post by devkurniadi on 2012-09-13
josephmills :

> 
also can we see a 
 	Code:
 	sudo lsof | grep /var/lib/dpkg/lock 
what is locking it ?


after i write the code, terminal show this

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/devkurniadi/.gvfs
      Output information may be incomplete.
aptd      2048        root   11uW     REG        8,5        0    1187713 /var/lib/dpkg/lock

---

### Post by devkurniadi on 2012-09-13
> **jerrrys said:**
> Do you have another package manager open while trying to use apt-get (like maybe the software center)?  You can have only one open at a time.


LOL! i don't know that only one can open at a time..
i'm new ubuntu user :D

---

### Post by josephmills on 2012-09-13
> **devkurniadi said:**
> josephmills :



after i write the code, terminal show this

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/devkurniadi/.gvfs
      Output information may be incomplete.
[COLOR="Red"]aptd      2048        root   11uW     REG        8,5        0    1187713 /var/lib/dpkg/lock[/COLOR]


 > [COLOR="red"]aptd[/COLOR]  allows  to  perform  package management tasks, e.g. installing or removing software, using a D-Bus interface. The privileges are  handled by  PolicyKit  so  the  client application doesn't need to run as root.
Furthermore aptd is started by D-Bus activation only when an user calls a method.**

 


You should be able to kill the daemon and so lets see the pid that it is running 

in terminal type 
```
ps aux | grep [a]ptd
```

then paste the out put please 

**source: Man page

---

### Post by jerrrys on 2012-09-13
been there, done that :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by devkurniadi on 2012-09-13
**josephmills** :

in ubuntu software center, I'm still downloading a software, whether it is the cause??

---

### Post by grash on 2012-09-13
Yes. That is the cause...

---

### Post by tienlbhoc on 2012-09-14
only need :
sudo nautilus

go to this folder and remove lock file

---

