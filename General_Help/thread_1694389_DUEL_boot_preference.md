---
title: "DUEL boot preference"
date: 2011-02-24
forum: General Help
---

### Post by rahulbest on 2011-02-24
I installed ubuntu on my pc recently...But problem is that i have windows XP too..and my dad is not comfortable with ubuntu so i want my default OS as WINDOWS XP in duel boot....
how i can do that????
PLEASE help....thanks in advance

---

### Post by migs73 on 2011-02-24
Install this using terminal (Ctrl+Alt+T)
```
sudo apt-get install startupmanager
```

type in your password when prompted (nothing will appear as you type, this is normal) and hit enter. Once it has finished installing go to;

 System > Administration > StartUp-Manager 

and there you can set the default OS to boot into and the time delay before it does so.

Mike

---

### Post by seawolf167 on 2011-02-24
You'll want to change the GRUB2 menu order

Open a terminal

Applications -> Accessories -> Terminal

Edit the GRUB2 config file

```
sudo gedit /etc/default/grub
```change the line 

```
GRUB_DEFAULT=0 
```to the position you want as default (say Windows is menu item #6, change the value to 5 [since counting starts at 0 not 1])

then save the file and exit, then update grub

```
sudo update-grub
```EDIT: Found a good [GRUB2 how-to link ]("http://ubuntuforums.org/showthread.php?t=1195275")in the forum archives (read the second bullet point in section #5)

---

### Post by rahulbest on 2011-02-24
I started using ubuntu recently....But prob is that at my place every one is familiar with windows so i kept duel boot....but i want Windows xp as default system and ubuntu 2nd...so wen pc starts it should go to windows xp directly right now its exactly opposite...
please help me.....thanks in advance

---

### Post by Kirboosy on 2011-02-24
There is a tool called "Startupmanager" that will allow you to easily change it)

Open Synaptic (System -->Admin-->Synpatic Package Manager)

Inside the Quick Search box type in "startupmanager" and select the package to install.

Once its done close Synaptic and go to System-->Admin-->StartupManager


Once inside you can lower your GRUB timeout and select your default boot selection. :D


~Caboose

---

### Post by seawolf167 on 2011-02-24
You posted this before and got the same answer

[http://ubuntuforums.org/showthread.php?t=1694389](http://ubuntuforums.org/showthread.php?t=1694389)

---

### Post by Ditchdoc7893 on 2011-02-25
I have a similar setup on my main desktop machine with Windows XP and Ubuntu, but it has multiple hard drives.  Because I have each OS on a different drive, I can boot either OS easily using the boot menu when the system starts up and simply selecting which hard drive I want to boot first and that in turn boots my OS of choice.  I did this strictly for simplicity, since my husband hasn't quite gotten comfortable with Ubuntu yet, and I have much still to learn.  I know this is a pretty easy fix, but it does work with minimal headache.  :)

---

