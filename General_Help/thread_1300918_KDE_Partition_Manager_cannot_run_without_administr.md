---
title: "KDE Partition Manager cannot run without administrative priviledges"
date: 2009-10-25
forum: General Help
---

### Post by nmyrick on 2009-10-25
Can someone tell me exactly what I need to enter in to the terminal in order to run KDE Partition Manager with administrative priviledges?:confused:

---

### Post by SuperSonic4 on 2009-10-25
> **nmyrick said:**
> Can someone tell me exactly what I need to enter in to the terminal in order to run KDE Partition Manager with administrative priviledges?:confused:

```
kdesu partitionmanager
```

FYI: You need to be root because messing about with partitions can be a very dangerous thing and is a system-wide change

---

### Post by nmyrick on 2009-10-25
Thank you.  I managed partitions many times before, but just in WinDoze.  I am a new user of Ubuntu.:guitar:

---

### Post by nmyrick on 2009-10-25
kdesu partitionmanager does not work.  I'm still getting "kdesu: command cannot be found".

---

### Post by nmyrick on 2009-10-25
I'm about to ditch KDE Partition Manager because of this problem.  When I start GParted Partition Editor, it automatically prompts me for a password to perform administrative tasks.  Why doesn't KDE do the same?  

The only reason I installed KDE is because it has complete partition backup capability, but this is really a pain.

---

### Post by SuperSonic4 on 2009-10-25
You really shouldn't do this but either ```
kdesudo partitionmanager
``` ```
sudo partitionmanager
```

---

### Post by VolkerLanz on 2009-10-25
> **nmyrick said:**
> I'm about to ditch KDE Partition Manager because of this problem.  When I start GParted Partition Editor, it automatically prompts me for a password to perform administrative tasks.  Why doesn't KDE do the same?  

It does. If you ran KDE Partition Manager from the KDE Desktop, KDE would indeed ask you for your password to gain root privileges (provided it's installed correctly). If you insist on running it from a shell, you're on your own ;-)

As others have said before, the correct command for (K)Ubuntu is

```
$ kdesudo partitionmanager
```

HTH.

---

### Post by nmyrick on 2009-10-25
I'm running it from the desktop, but the only options it gives me are to cancel the operation, or run without administrator priviledges.  Then if I run without admin priviledges, it starts, but won't let me do anything.  I'm going to try to reinstall it, maybe that is the issue.

---

### Post by nmyrick on 2009-10-25
I'm running the GNome desktop environment.  Why won't it work in this environment?

---

### Post by SuperSonic4 on 2009-10-27
You may not have the kdesu or kdesudo packages installed. What is the output of ```
ls /usr/bin | grep kdesu
```

---

### Post by Globespy on 2009-12-25
I am new to Linux and Ubuntu - like what I see so far.
After a clean and successful installation I want to be able to create a bootable image of my install to a DVD so that I can quickly restore if I screw something up or something happens with the HDD.
I can't seem to find an application that will do this easily from a bootable disk (like Acronis true Image for Windows), so I wanted to try the PING route.  It's more complicated than I had expected and the first thing is to create a new partition to store the image since PING does not seem to have the functionality to save directly to a DVD from within the image creation process - I have to save the image first to a partition and then burn the ISO.
I have tried to use both KDE Partition Manager and Gparted but even when I run the programs from a terminal I get the same error messages in both.  I believe I am running as root, but hope someone can help me. Where should I create the partition and how can I access a partition program correctly where it will allow me to create a partition?  OR IF THERE"S AN EASIER WAY TO CREATE AN IMAGE TO DVD!!!  Here is a typical screen dump from a terminal when I try to access a partition manager program, in this case Gparted:

globespy@globespy-pc:~$ sudo bash
root@globespy-pc:~# kdesedu gparted
kdesedu: command not found
root@globespy-pc:~# kdsedu gparted
kdsedu: command not found
root@globespy-pc:~# kdsedu gparted
kdsedu: command not found
root@globespy-pc:~# kdesudo gparted
[B]Error: "/var/tmp/kdecache-globespy" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-globespy" is owned by uid 1000 instead of uid 0[/B].
======================
libparted : 1.8.8.1.159-1e0e
======================
^C
root@globespy-pc:~# c

---

### Post by SuperSonic4 on 2009-12-25
You are running as root, if you're connected to an x-server you may not need kdesudo but it's not wise

Better is to switch to a normal user ```
su - *user*
``` and then run ```
kdesudo partitionmanager
``` or ```
gksu gparted
``` as user since user has access to X

You may be able to use cfdisk as root from the terminal and then format it but I'm not sure if that'd help

---

### Post by Globespy on 2009-12-25
Firstly, thanks for the FAST reply, and Happy Holidays!
I tried your suggestion, did not work.
I then created a new user account with admin privilages.
I then switched users to that new user account and proceeded to install KDE Partition manager. I tried to run the application but got the same error about needing admin privilages.
So I opened a terminal wnidow and tried the following without result - I cannot create new partiions or gain access to these controls:
sean1972@globespy-pc:~$ kdesedu partitionmanager
kdesedu: command not found
sean1972@globespy-pc:~$ sedu partitionmanager
No command 'sedu' found, did you mean:
 Command 'sed' from package 'sed' (main)
sedu: command not found
sean1972@globespy-pc:~$ sudo partitionmanager
[sudo] password for sean1972: 
error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourself
Error: "/var/tmp/kdecache-sean1972" is owned by uid 1001 instead of uid 0.
Error: "/tmp/kde-sean1972" is owned by uid 1001 instead of uid 0.

---

### Post by nmyrick on 2009-12-25
Dear Globespy,

First of all, welcome to Linux!

Here's something you will be glad to hear.  If you are just trying to make sure that you have a good backup, you don't need to create images at all!

All you have to do is use "File Backup Manager" to backup your home directory to a USB drive on a regular basis.  Then, if you do have an issue where your hard drive crashes, all you have to do with the new hard drive is install Ubuntu from the live CD, then replace the default home directory with your backup home directory (copy and paste), then restart your computer, and that is it!!  All of your installed programs and updates will be there, since they are all stored in the home directory.

That is why it is recommended that when you install Ubuntu, you should actually install the OS on one partition (approx 7 GB), then create a second partition for your Home directory.  Then, when new Ubuntu OS's are released, can just swap out the OS on the primary partition, and all of your settings and programs that you have installed on the previous OS will still be there with the new OS.  

This is one of the glory's of the file structure of Linux!  You don't have to image your drive, or experience all of the problems with WinDOZE Backup programs.

Happy Holidays! 

NMyrick

---

### Post by nmyrick on 2009-12-25
Please correct me if I'm wrong, but I do not think the KDE Partition Manager will run in the GNome desktop environment.  This may be the problem that Globespy is having.  But, like I said before, you really don't need to create images for backup anyway.  You just need to backup your home directory.

---

### Post by VolkerLanz on 2009-12-27
> **nmyrick said:**
> Please correct me if I'm wrong, but I do not think the KDE Partition Manager will run in the GNome desktop environment.

This is indeed wrong. KDE Partition Manager will run just fine in a Gnome environment. There's one catch: Gnome does not understand how to ask for an admin password when KDE applications are run from the menu, so it just doesn't do it. So under Gnome one has to run it with gksu or kdesudo from a terminal, just like stated above.

From version 1.0.1 on KDE Partition Manager will fix this problem by asking for the admin password itself to accommodate Gnome users.

---

### Post by Zorael on 2009-12-27
FWIW, Kubuntu (alone?) renames the kdesu binary to **kdesudo**, for reasons beyond me. Perhaps to make it consistent with the terminal sudo.

I see some 'kdesedu's in the terminal output snippets, which obviously won't work. Just remember the mnemonic "**KDE SuperUser Do**" and you'll get it right.

I always symlink kdesudo to kdesu, but mostly because I'm used to using kdesu.
```
$ sudo ln -s /usr/bin/kdesudo /usr/local/bin/kdesu
```

---

### Post by cabaro on 2009-12-27
```
sudo su -
```
```
partitionmanager
```

or

```
sudo su -
```
```
gparted
```

---

