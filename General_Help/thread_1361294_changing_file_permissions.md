---
title: "changing file permissions"
date: 2009-12-21
forum: General Help
---

### Post by FarmBoy72 on 2009-12-21
Ok, so i am trying to change some file permissions with chmod, but i get the message: Operation not permitted
using;

user@SmartQ:~$ chmod -r /usr/share/icons/ -rwxrwxrwx

How can i give myself permission to do this. I want to be able to do anything and everything without running into "Permission Denied", even if it will kill my OS.

Any help is greatly appreciated -THANKS!

---

### Post by spiderbatdad on 2009-12-21
that directory is root owned, so don't go changing the permissions. Instead become root or use sudo to accomplish the actual task you want to accomplish...which is what?

---

### Post by FarmBoy72 on 2009-12-21
Well on this device it logs you in automatically when it boots, so i have no idea who im logged in as. and i was trying to put files in the icons folder but it would not let me, so i looked at the permissions and it says the owner can do everything but the others can read/execute but not write. so it makes me think im logged in as user. and i want to give the user account all the permissions of owner since i cant "login" as the owner.

---

### Post by spiderbatdad on 2009-12-21
try ```
sudo -i
```to start a root terminal session. If you prefer to work graphically, try ```
gksu nautilus
``` You can break things in either mode if you don't know what you're doing. Also ```
 id 
``` will show you who you are logged in as.

---

### Post by FarmBoy72 on 2009-12-21
If i break things it only takes 2 min to re-flash the os.

---

### Post by FarmBoy72 on 2009-12-21
well the device logs in as user, is there any possible things to try that can make the device login as owner?

---

### Post by spiderbatdad on 2009-12-21
the "device" is sounding suspiciously like someone elses computer.

---

### Post by FarmBoy72 on 2009-12-21
No its a SmartQ V7 MID not someone elses PC (see attachment)

---

### Post by lukeiamyourfather on 2009-12-21
Looking at the directory path its probably owned by root. Changing the ownership to a user besides root is not a good idea, especially if you don't know what you're doing. Use "sudo" to run a command as root in Ubuntu. If its not Ubuntu you might have to become root first and then run commands. The command "su" will switch the current user to root for that terminal session. You will need the root password to do this. If you don't have the root password then you can't modify the files.

---

### Post by FarmBoy72 on 2009-12-21
well im screwed, the password is probably in chinese

also, im not trying to change the owner, just trying to give user permission to write

---

### Post by spiderbatdad on 2009-12-21
sorry for misunderstanding and still looking. apparently a firmware upgrade to v4.0 fixed a previous problem...which was unable to login as root. Is your firmware up to date. lol. still don't know how to login as root though.

---

### Post by FarmBoy72 on 2009-12-21
Firmware is at version 5.2 latest update, (replaces 5.1 wich is a miserable FAIL)

i also need to remove a few startup programs, such as Wbar (wbar is the shortcut bar across the bottom of the mid) it gets in the way of everything, theres no point to it except to use up memory. all it does is open programs which i can access via the mainmenu

i know where the wbar program is located, can i just delete it or should i remove its name form a file somewhere that starts the program on bootup

---

### Post by spiderbatdad on 2009-12-21
[http://android.gval.biz/](http://android.gval.biz/)

---

### Post by FarmBoy72 on 2009-12-21
That would help out alot if i was using android, lol it has 3 OS's so its hard to tell which one people are talking about, im in the UBUNTU - based OS, the android is experimental and freezes upon booting. also, ive been able to get root access but when i try to change the file permissions it gives me this message: 

mode of '/usr/share/icons' retained as 0000 (----------)

---

### Post by FarmBoy72 on 2009-12-22
OK i figured out my problem, it just didnt like the way i was typing things in.

---

