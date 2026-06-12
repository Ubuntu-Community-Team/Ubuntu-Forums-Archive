---
title: "Install Problem Warning"
date: 2011-03-17
forum: General Help
---

### Post by Ndjanahaar on 2011-03-17
Dear all,
I was trying to Recover some lost data from an external hard drive. It went well but when I tried to restart my laptop, it shows a message saying: INSTALL PROBLEM, THE CONFIGURATION DEFAULT FOR GNOME POWER MANAGER HAS NOT BEEN INSTALLED CORRECTLY - PLEASE CONTACT YOUR COMPUTER ADMINISTRATOR. The problem is then, when I'm trying to log on it never finishes but keep giving me the login window. 
If anyone has an idea on how to solve my problem, please help.
Thx indeed
I'm using Ubuntu 10.10, Environment GNOME

---

### Post by pastalavista on 2011-03-17
Press and hold the 'Shift' key while booting to access the grub boot-loader screen. Select 'recovery mode' and 'repair broken packages'

Welcome to Ubuntu. We do things different around here... better!

---

### Post by Ndjanahaar on 2011-03-17
> **pastalavista said:**
> Press and hold the 'Shift' key while booting to access the grub boot-loader screen. Select 'recovery mode' and 'repair broken packages'

Welcome to Ubuntu. We do things different around here... better!


Thx indeed pastalavista for your post. I tried your suggestions and what I got is many failure to access many websites needed for the repair. And the same problem remain when trying to log on. Any further advice please?
Thx

---

### Post by pastalavista on 2011-03-17
> **Ndjanahaar said:**
> Thx indeed pastalavista for your post. I tried your suggestions and what I got is many failure to access many websites needed for the repair. And the same problem remain when trying to log on. Any further advice please?
Thx
I believe the only way to repair it now is to reinstall. Try without reformatting (or losing data) by booting up the install disk or flash drive (try without installing) to the desktop, click the install icon on the desktop and enter all the same information exactly like the original installation but when you get to the partition setup. select manual mode and you'll see the original setup. Mount all the partitions in the same place as before but be sure to UNCHECK all the 'format' boxes. It shouldn't take long but you'll need to do all the updates again too.

---

### Post by Krytarik on 2011-03-17
Please try the following:
- boot into "recovery mode"
- choose "root shell prompt"
- enter
```
sudo dpkg --configure -a
```- confirm the dialog that might come up (navigate with TAB and/or arrow-keys, select with SPACE, confirm with Return/Enter)
- reboot (Ctrl+Alt+Del)

---

### Post by Ndjanahaar on 2011-03-17
> **Krytarik said:**
> Please try the following:
- boot into "recovery mode"
- choose "root shell prompt"
- enter
```
sudo dpkg --configure -a
```- confirm the dialog that might come up (navigate with TAB and/or arrow-keys, select with SPACE, confirm with Return/Enter)
- reboot (Ctrl+Alt+Del)


I have tried your suggestion as well, this is the message I got:
dpkg: unrecoverable fatal error, aborting: unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on the device

My question is: Is there any possibility to RESTORE my system for previous status? I want to know that before I proceed to reinstall the whole system.
Thanks for your help.

Ndjanahaar

---

### Post by Krytarik on 2011-03-17
> **Ndjanahaar said:**
> 
dpkg: unrecoverable fatal error, aborting: unable to fill /var/lib/dpkg/updates/tmp.i with padding: **No space left on the device**

Did you notice that?! It seems like the root partition is full.

Boot like before and check the disk usage with those command:
```
df -Th
```
Guide: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by Ndjanahaar on 2011-03-17
> **Krytarik said:**
> Did you notice that?! It seems like the root partition is full.

Boot like before and check the disk usage with those command:
```
df -Th
```Guide: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)


You are right indeed. It shows 0% Available space on disk, 100% used. What should I do then in order to liberate my disk space?

---

### Post by Krytarik on 2011-03-17
> **Ndjanahaar said:**
> You are right indeed. It shows 0% Available space on disk, 100% used. What should I do then in order to liberate my disk space?
1.) What is the actual usage of your root partition? For example, mine is just 4.5 GB.

2.) Those command may be useful to clear the package cache:
```
sudo apt-get clean
```
3.) Follow the mentioned guide to find possible culprits.

---

### Post by Ndjanahaar on 2011-03-18
Dear all,
Thank you very much for your help to solve my problem. What I actually did was: booting with a LIVE CD and then took all my precious files from my laptop, changing the permission in order for me to copy them into another device and then I am going to reinstall my system. Once again, thank you all very much.

Ndjanahaar

---

