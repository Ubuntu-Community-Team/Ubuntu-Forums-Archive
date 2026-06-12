---
title: "ubuntu 9.10 desktop tty1"
date: 2010-01-26
forum: General Help
---

### Post by dinw3 on 2010-01-26
hi , i am facing a problem with my  start up GUI . The system drop me to terminal 
**_ubuntu 9.10 desktop tty1_** 
any steps should i followed to revert my GUI ? 
Thanks

---

### Post by n0dix on 2010-01-26
You have gdm run?? look the .xsession_error in your $HOME for an error or something.

---

### Post by dinw3 on 2010-01-26
How i do that ? please

---

### Post by adam814 on 2010-01-26
Log in as you would through the GUI.  You can shut down by typing "sudo reboot"

At the GRUB menu you should have a recovery mode option and it will boot to a menu giving you several options.  I believe the one you want is labeled xfix.  If not it should be self-explanatory.

---

### Post by n0dix on 2010-01-26
Loggin in console tty, and type:
1. **Running gdm:** ```
sudo /etc/init.d/gdm start
```
2. **See .xsession_error:** ```
nano ~/.xsession_error
```

---

### Post by dinw3 on 2010-01-27
> **adam814 said:**
> Log in as you would through the GUI.  You can shut down by typing "sudo reboot"

At the GRUB menu you should have a recovery mode option and it will boot to a menu giving you several options.  I believe the one you want is labeled xfix.  If not it should be self-explanatory.

there is no grub menu in my system , it may deleted for some reason . I followed your step and i didnt see the grub menu , the only thing is a desktop tty1 .

---

### Post by dinw3 on 2010-01-27
> **n0dix said:**
> Loggin in console tty, and type:
1. **Running gdm:** ```
sudo /etc/init.d/gdm start
```2. **See .xsession_error:** ```
nano ~/.xsession_error
```

i didnt see the error , any other ideas .

---

### Post by dinw3 on 2010-01-27
Rather than invoking init script through /etc/init.d, use the service utitlity service gdm start
 Since the script you are attempting to invoke has been converted to an upstart job, you may also use the start  utility, eg start gdm 
gdm start/running , process 1748

---

### Post by adam814 on 2010-01-27
> **dinw3 said:**
> there is no grub menu in my system , it may deleted for some reason . I followed your step and i didnt see the grub menu , the only thing is a desktop tty1 .
You should be able to get the menu to display holding down the shift key while it boots.  It's there or you wouldn't get as far in the boot process as you do.

---

### Post by dinw3 on 2010-01-28
> **adam814 said:**
> You should be able to get the menu to display holding down the shift key while it boots.  It's there or you wouldn't get as far in the boot process as you do.
nothing happen , still i get tty1 . 
any way to access my files like home directory and Firefox bookmarks , i am going to reinstall the version .

---

### Post by adam814 on 2010-01-28
Sure, login at the terminal and use any one of the usual commands to copy things to a safe place.  I'd suggest if you have a big enough external drive to hold the contents of your home directory that you do something like this:

Assuming your external drive is /dev/sdb1 and it's mounted on /media/disk, verify this with "sudo fdisk -l" (that's a lower-case L) and "mount | grep sdb1":
```
tar cvjf /media/disk/homebackup.tar.bz2 $HOME
```

Then after you reinstall:
```
tar xvjpf /media/disk/homebackup.tar.bz2 -C $HOME
```

---

### Post by dinw3 on 2010-01-31
what i did is this : 
- install ubuntu 9.10 again side with the pervious install ubuntu  9.10 
- Then , i click on " places " and notice " 13 GB filesystem " which is the previous installtion and my all files there and starting copying importing files .

My Question : where i can access my firefox bookmarks in linux system ?

---

### Post by n0dix on 2010-01-31
> **dinw3 said:**
> 

My Question : where i can access my firefox bookmarks in linux system ?

In your home folder &#8594; Ctrl + H (ot View &#8594; Show Hidden Files) &#8594; .mozilla &#8594; firefox &#8594; something.default (something = mad mixture of letters and numbers) &#8594; bookmarks.html

---

