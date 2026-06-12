---
title: "Terminal problems, sudo is not working"
date: 2011-01-11
forum: General Help
---

### Post by Caperalis on 2011-01-11
Right now im trying to edit the partitions so that i can remove windows and fill up that space with Linux.Ubunto and get rid of windows.

I started with 

sudo -i
gedit /boot/grub/menu.lst

in the terminal.
Then it asks for the sudo password.
Then it won't let me type anything.. 
And thats what the problem is

---

### Post by CoolJohnB on 2011-01-11
Do you type in your password?  When you type it in you don't see anything as it doesn't show - just type in your password and hit enter.

---

### Post by hhh on 2011-01-11
What in the world? Use Gparted to repartition. Use gksu gedit to open gedit with administrator privileges. Learn about partitioning before you do anything. Editing your Grub configuration isn't going to remove Windows, just the option to boot into it.

BTW, how low on disc space are you? I don't understand why people remove Windows when disc space is so cheap, they paid for the OS and it may come in handy down the line.

---

### Post by Caperalis on 2011-01-11
If I type in the password, and it enter, it says incorect password.
And nothing shows up when I type


Also I could not find or Install GParted.
And my Synaptic Package thing is down due to the sudo problem


My windows is killing itself slowly.
And I would like that space. if not to remove it at least make the windows partition smaller.
i have no clue how much space Ubuntu is using though

---

### Post by CoolJohnB on 2011-01-11
It might be easier to backup up your data and reinstall Ubuntu when doing the installation just choose to use the whole disk, and remember your password!

---

### Post by Caperalis on 2011-01-11
I got the password thing fixed...
Typed to quickly. and such..
Now Im getting a problem with the synaptic package thing

Fk. Now its working again..

I don't know what's wrong with it :P..

Where would I go to learn about Partitioning?

---

### Post by Caperalis on 2011-01-11
> **CoolJohnB said:**
> It might be easier to backup up your data and reinstall Ubuntu when doing the installation just choose to use the whole disk, and remember your password!



Yeah..
Sounds like a good idea. 

I was going to do that before.

but nothing was working properly.

and I installed ubunto from the windows partiton.
so if i just reinstall it and select whole disk
problem = solved?

---

### Post by WorMzy on 2011-01-11
If you installed via Wubi onto the Windows partition, then you may be mistaken about the low disk space warning. What Wubi installations think is your "disk" is actually a single file on the Windows partition where it stores it's files; when this file is close to being full, Ubuntu tells you your disk is nearly full, when in reality, only the file is nearly full.

Installing Ubuntu properly, to it's own dedicated partition, is the best course of action in this event, and, depending on the fullness of your actual hard disk, deleting Windows may not be necessary.

One more thing: you cannot delete Windows if you installed via Wubi. Wubi is installed inside Windows, so deleting Windows will delete both operating systems.

---

### Post by hhh on 2011-01-11
WorMzy is right, we need to know what "from the Windows partition" means. Boot into Windows and see if "Ubuntu" or "Wubi" is listed in Control Panel>>Add/Remove Programs. If it is, you'll probably want to save your Home folder data and uninstall Ubuntu and do a "real" installation. Some links for more info...
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

