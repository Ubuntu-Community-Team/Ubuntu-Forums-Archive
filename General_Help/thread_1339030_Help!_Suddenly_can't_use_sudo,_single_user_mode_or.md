---
title: "Help! Suddenly can't use sudo, single user mode or root!"
date: 2009-11-27
forum: General Help
---

### Post by tammer on 2009-11-27
While messing around with my iPod with Banshee and Songbird of all things, my Karmic installation suddenly stopped recognizing my user as a sudoer. When typing any sudo commands, I get this:

tammer is not in the sudoers file.  This incident will be reported.

I can't su, and the root password has somehow changed so I can't set my user as an admin through the users & groups settings. Also, I've tried booting into single user mode, but for some reason pressing shift at boot (I'm using grub 2) doesn't activate it and it just boots normally. :(

---

### Post by nothingspecial on 2009-11-27
Boot into recovery mode (root shell) and type ```
adduser username admin
```

Change username for your username.

---

### Post by nerdopolis on 2009-11-27
In your system run the command.
```
df / | awk '{print $1}' | grep /

```

This will return the device name of your root file system. (for example mine is /dev/sda1). write down the device name.

In a live cd run 
```
sudo mount <device name from first command> /media 
``` . sudo will work in the live cd. This command will mount your root file system in the /media folder.

once you mounted the root file system, run 
```
sudo chroot /media
``` . once you run that command the prompt will change from ubuntu@ubuntu to root@ubuntu. Chroot will run bash from the specified folder. It will run /media/bin/bash. In that new bash shell, if you run 
```
ls /
``` , it will be the contents of your root file system.  Any command you run within that new bash prompt will run within your system.

you can now run ```
passwd
```, to change the root password, 

and you can run the command **nothingspecial** suggested. 

Be aware that you can't really run graphical programs within chroot, without a little trickery. But you shouldn't need graphical programs to do what you're doing. If you do need them, let me know, and I'll tell you how to do it.

---

### Post by tammer on 2009-11-27
Ah, thank you for all your help. For some reason last night I was unable to boot into recovery mode, but today I was able to and use the command nothingspecial mentioned. If anyone else encounters this problem, just make sure you're pressing shift early enough. Thanks again!

---

