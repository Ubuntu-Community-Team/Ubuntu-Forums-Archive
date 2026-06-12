---
title: "How can I become master of my domain????"
date: 2006-04-06
forum: General Help
---

### Post by BobInIdaho on 2006-04-06
I want to move a file or two but the program keeps telling me I do not own that directory. How can I become owner of the entire system??? Just long enough to do what I gotta do...???? Breezy 5.10 under Gnome....

Bob](*,)

---

### Post by rado_london on 2006-04-06
As far as I get your point you want to have permissions for the whole /. Well only root can do that. There is an options to use your normal user as root. To do that put "sudo" without the quotes before each command.
Example:
```
sudo apt-get update
```

Than it will ask you for a password. Just type in your user password.

Hope this helps

---

### Post by aysiu on 2006-04-06
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by BobInIdaho on 2006-04-06
Nope....those did'nt help. I WANT TO BE GOD as far as Ubuntu is concerned. I want to be able to wreck havoc on the system if I want to....Like Windose...I want to be able to move any file...anywhere I choose...no questions asked..

Bob](*,)

---

### Post by Azrael on 2006-04-06
[quote=BobInIdaho]Nope....those did'nt help. I WANT TO BE GOD as far as Ubuntu is concerned. I want to be able to wreck havoc on the system if I want to....Like Windose...I want to be able to move any file...anywhere I choose...no questions asked..

Bob](*,)[/quote]
sudo (you can also do *sudo su* for convenience*)* makes you "GOD" over your system. However, you might need to change ownership (*chown*) and/or permissions (*chmod*) before being able to access certain files. If you want to chown your entire system you can use the command recursively (bad idea!). Read the man, info pages, aysiu's link or google for more info.

---

### Post by drberg1000 on 2006-04-07
[QUOTE=BobInIdaho]Nope....those did'nt help. I WANT TO BE GOD as far as Ubuntu is concerned. I want to be able to wreck havoc on the system if I want to....Like Windose...I want to be able to move any file...anywhere I choose...no questions asked..

Bob](*,)[/QUOTE]

First, this is not recommended for various reasons of security and killing your system.  

To beable to login as root you simply need to give that account a password.

In a terminal run 

```
sudo passwd
```

Enter your password.  Twice.  and choose something secure if your on an untrusted network (ie connected to internet).

Now you can su to root and use it all you want.  To log into Gnome as root (this is doubly not recommended) you will probably need to play with settings in [System]->[Administration]->[Login WIndow].  User root isn't specifically excluded under the users tab, so you may be able to just log in.  The "allow local system adminstrator login" may need to be checked on the Security tab.  I'm not sure, and I'm not going to try to find out.  Opens up too many potential holes.

--Dave

---

