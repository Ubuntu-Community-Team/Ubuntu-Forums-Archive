---
title: "Omg"
date: 2006-05-24
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-24
OMG im really getting annoyed with this now im still cant get nvidia drivers properly yes i have univers and multiverse etc etc but when i get so far in the process it FUX up on me have a read at what i have done can any one tell what i have done wrong



```
root@dappertest:/home/daniel# apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-kernel-source
The following packages will be REMOVED
  nvidia-settings
The following NEW packages will be installed
  nvidia-glx
0 upgraded, 1 newly installed, 1 to remove and 18 not upgraded.
Need to get 0B/4052kB of archives.
After unpacking 11.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 71163 files and directories currently installed.)
Removing nvidia-settings ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 71150 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8756+2.6.15.10-2_i386.deb) ...
Setting up nvidia-glx (1.0.8756+2.6.15.10-2) ...

root@dappertest:/home/daniel# sudo apt-get install nvidia-settings
sudo: /etc/sudoers is mode 0777, should be 0440
root@dappertest:/home/daniel# apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  nvidia-glx
The following NEW packages will be installed
  nvidia-settings
0 upgraded, 1 newly installed, 1 to remove and 18 not upgraded.
Need to get 0B/504kB of archives.
After unpacking 11.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 71194 files and directories currently installed.)
Removing nvidia-glx ...
Selecting previously deselected package nvidia-settings.
(Reading database ... 71150 files and directories currently installed.)
Unpacking nvidia-settings (from .../nvidia-settings_1.0-3ubuntu7_i386.deb) ...
Setting up nvidia-settings (1.0-3ubuntu7) ...

root@dappertest:/home/daniel# cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
root@dappertest:/home/daniel# nvidia-glx-config enable
bash: nvidia-glx-config: command not found
root@dappertest:/home/daniel#

```

---

### Post by LORD_PoLvO on 2006-05-24
had a quick read thru again hmm it is deleting the each is deleting teh other when i try to install when i do glx it delets settings when i do settings it delets glx?

---

### Post by dmizer on 2006-05-24
that's absolutely right ... i was going to point that out.

found this in another post:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
You may have to reboot for changes to take effect.

---

### Post by LORD_PoLvO on 2006-05-24
kk ty im about to give that a try lol

---

### Post by LORD_PoLvO on 2006-05-24
bugger never had this error b4 ne insight ?


```
root@dappertest:/home/daniel# apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-kernel-source
The following packages will be REMOVED
  nvidia-settings
The following NEW packages will be installed
  nvidia-glx
0 upgraded, 1 newly installed, 1 to remove and 18 not upgraded.
Need to get 0B/4052kB of archives.
After unpacking 11.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 71163 files and directories currently installed.)
Removing nvidia-settings ...
Selecting previously deselected package nvidia-glx.
(Reading database ... 71150 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1.0.8756+2.6.15.10-2_i386.deb) ...
Setting up nvidia-glx (1.0.8756+2.6.15.10-2) ...

root@dappertest:/home/daniel# nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
root@dappertest:/home/daniel#

```

---

### Post by LORD_PoLvO on 2006-05-24
did nano /etc/X11/xorg.conf and changed the nv to nvidia still no difference

---

### Post by dmizer on 2006-05-24
that error is just telling you that nvidia-glx-config enable did what it was suppose to do ... that is, to change your xorg.conf.

try running nvidia-glx-config enable again, ignore the error and reboot.  be prepared to edit your xorg.conf in shell in case your reboot doesn't bring x up again.

edit:
that's probably about as far as i'm going to be able to take this, as i neither have nvidia nor do i have dapper.

---

### Post by LORD_PoLvO on 2006-05-24
okies got that umm what do i edit in the xorg if it fails to bring up the x desktop i no i should be abble to aces it doing nano /etc/X11/xorg.conf but hwat do i chage in it whilst i am there?

---

### Post by dmizer on 2006-05-24
[QUOTE=LORD_PoLvO]nano /etc/X11/xorg.conf[/QUOTE]
that's how you edit xorg.conf.

heh ... you edited your post ;)

if it won't work, change the nvidia driver back to nv.

---

### Post by LORD_PoLvO on 2006-05-24
yeah i was asking wat do i change in xorg when i have it open if x desktop disent load?

---

### Post by dmizer on 2006-05-24
[QUOTE=LORD_PoLvO]yeah i was asking wat do i change in xorg when i have it open if x desktop disent load?[/QUOTE]
see my edited post.

---

### Post by LORD_PoLvO on 2006-05-24
okies well im about to dive into the unknown for a few mins hopefully brb lol

---

### Post by LORD_PoLvO on 2006-05-24
well im back lol heh i get the nvidia logo now do i just continue install from the 
```
sudo apt-get install nvidia-settings
```

?

---

### Post by Perfect Storm on 2006-05-24
Aye, you might want to make launcher for it after you installed it.
The command line for it is:

nvidia-settings

after you installed it.

---

### Post by LORD_PoLvO on 2006-05-24
cant do nething atm read thread /etc/sudoers wrong????????

---

### Post by dmizer on 2006-05-24
from your earlier posts, it looks like you have a root account set up.  this is not normal for ubuntu, which is why everyone is suggesting "sudo".

i don't know how you ended up with a root account, but if you are logged in as root, you don't need sudo in front of your commands.

---

### Post by LORD_PoLvO on 2006-05-24
im used to seting up root so i dont have to go sudo all the time lol btw found the problem b4 i changed to folder etc permisions to 777 so i could change some scripts but i forgot to change back to 440 lol so once i had reset i couldnt get into root lol so luckily i still had my breezy in and i could mount dapper and change it back to 440 from there lol using chmod lol

---

### Post by dmizer on 2006-05-24
[QUOTE=LORD_PoLvO]im used to seting up root so i dont have to go sudo all the time lol btw found the problem b4 i changed to folder etc permisions to 777 so i could change some scripts but i forgot to change back to 440 lol so once i had reset i couldnt get into root lol so luckily i still had my breezy in and i could mount dapper and change it back to 440 from there lol using chmod lol[/QUOTE]
setting up root just so you don't have to type "sudo" is a bad idea.

edit to add: btw, running as root (administrator) is what got windows users in trouble.

---

### Post by LORD_PoLvO on 2006-05-24
[QUOTE=dmizer]setting up root just so you don't have to type "sudo" is a bad idea.

edit to add: btw, running as root (administrator) is what got windows users in trouble.[/QUOTE]


wats wrong with running in root because when u have lots of files to insatll it saves heaps of time

---

### Post by Gustav on 2006-05-24
[QUOTE=LORD_PoLvO]wats wrong with running in root because when u have lots of files to insatll it saves heaps of time[/QUOTE]
You can use 'sudo -i' to achive the same effect as having a root account and doing 'su'.

---

### Post by LORD_PoLvO on 2006-05-24
kk

---

### Post by dmizer on 2006-05-24
[QUOTE=LORD_PoLvO]wats wrong with running in root because when u have lots of files to insatll it saves heaps of time[/QUOTE]
it only saves maybe a couple of seconds.  once you type in your password after sudo, it remembers for a period of time so you don't have to retype the password.

as i said in my edited post, running as root is what puts windows users in trouble.  anything/body can just do whatever they want on your computer.  to say nothing of the damage you can cause yourself.

there's a very descriptive explination running around somewhere, but i'm having difficulty putting my finger on it.  but i'm sure someone else can oblige.

---

