---
title: "Changing the machine name in 9.10"
date: 2009-10-22
forum: General Help
---

### Post by Saros Thaine on 2009-10-22
I just got started with 9.04 a few weeks ago and just updated to 9.10. The problem I am having is figuring out how to change the name of the machine. I have found a few references to changing it under older versions of Ubuntu but none seem to work with the latest versions.  Thanks

---

### Post by Giblet5 on 2009-10-22
```
sudo gedit /etc/hostname
sudo /etc/init.d/networking restart
```

That should do it.

---

### Post by RichardLinx on 2009-10-22
Open a terminal and type:
```
gksudo gedit /etc/hostname
```
You will be prompted for a password, type in your password. Then change the computer name in the text file and click save.

---

### Post by Saros Thaine on 2009-10-22
Thanks guys...that got it.

---

### Post by Geraba on 2009-11-23
I tried to edit those files... ok.
Then I tried to change the hostname using "hostname newname" on a terminal... Now, if I try to launch gedit, I get the error:

```

No protocol specified

(gedit:4574): Gtk-WARNING **: cannot open display: :0.0

```

Not only that, I can't open any program in the graphical interface....

I'm able to launch gedit using "sudo gedit" and then I undo what I done... but then how do I change my computer name without rendering it useless???

---

### Post by louieb on 2009-11-23
If you have been using sudo to open graphical programs - you may have changed the ownership of some configuration files to root. 

to check open a terminal window  . it should open in your home directory .
```
ls -la
```and look for files owned by root.  

That is one of the reasons you should use [COLOR=Red]**gksudo**[/COLOR] when you need to open a graphical program as administrator (root).

BTW: the 2 files you need to edit to change the computer name are /etc/hostname and /etc/hosts
for more information.
```
man hosts
man hostname
```

---

### Post by bodhi.zazen on 2009-11-23
> **louieb said:**
> BTW: the 2 files you need to edit to change the computer name are /etc/hostname and /etc/hosts

By editing only one you have now broken sudo, so you will need to boot to recovery mode or boot a live CD to fix your problem.

Be sure your hostname is listed in /etc/hostname and /etc/hosts.

In /etc/hosts list it in the 127.0.1.1 line, where you see your old hostname ;)

---

### Post by Geraba on 2009-11-24
> **louieb said:**
> If you have been using sudo to open graphical programs - you may have changed the ownership of some configuration files to root. 

to check open a terminal window  . it should open in your home directory .
```
ls -la
```and look for files owned by root.  

That is one of the reasons you should use [COLOR=Red]**gksudo**[/COLOR] when you need to open a graphical program as administrator (root).

BTW: the 2 files you need to edit to change the computer name are /etc/hostname and /etc/hosts
for more information.
```
man hosts
man hostname
```

I use gksudo to open graphical programs as root... I used it to open gedit so I could edit /etc/hosts and /etc/hostname... But when I did, gedit wouldn't open again with normal privileges neither with gksudo. Only sudo could launch it.

> **bodhi.zazen said:**
> By editing only one you have now broken sudo, so you will need to boot to recovery mode or boot a live CD to fix your problem.

Be sure your hostname is listed in /etc/hostname and /etc/hosts.

In /etc/hosts list it in the 127.0.1.1 line, where you see your old hostname ;)

I changed both at the same time... And I also changed the hostname after that using "sudo hostname newname"... 
Actually, I just tried it again, after I change both hosts and hostname AT THE SAME TIME, I can't launch any applications, not even a terminal... Luckily, I left gedit open to undo that ;)
Anyway... What could I be doing wrong?

EDIT: By leaving gedit open, I noticed the system changed it... it changed the line that contains 
127.0.0.1       localhost
to:
127.0.0.1    newname    localhost.localdomain    localhost

I guess this is causing the problem!!! But how to avoid it?

---

