---
title: "Mounting network drive permanently"
date: 2009-11-23
forum: General Help
---

### Post by simartem on 2009-11-23
I have a media console on the network and i can reach the device as in the following :
 
```

 
smb://192.168.5.23/hdd1/
 
or
 
smb://venus/hdd1/
 

```
 
I have put a shortcut on the desktop but, it doesnt connect if i dont go to nautilus and look at the network connections, i need to mount it first.. How can i set it a permanent mount as the computer starts ? Thank you

---

### Post by simartem on 2009-12-03
bump

---

### Post by Dinodoc on 2009-12-03
Sorry I can't really be of alot of help on this, never mounted smb, but you would need to edit the fstab file, google fstab for correct form and what have you.

**Helpful hint, before doing anything backup the original**

Google has this to offer - [http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

### Post by Dinodoc on 2009-12-03
So I think with your setup it would be something like, replacing what needs to be replaced of course:

**[FONT=monospace]//venus/hdd1 /where/to/mount smbfs[/FONT] ****[B]username=username,password=password 0 0** [/B]

---

### Post by callan79 on 2009-12-03
> **simartem said:**
> How can i set it a permanent mount as the computer starts ? Thank you



Hi simartem,

You should probably have a look at [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently), but to give you a quick overview ...


1. Make a new mount point :

```
sudo mkdir /media/venus
```

2. Open your fstab file so you can add the mount details

```
sudo nano /etc/fstab
```

3. Add the following line to the end of fstab :

```
//192.168.5.23/hdd1/ /media/venus cifs auto,nounix,noserverino,user=VENUSUSER,password=VENUSPASS,uid=UBUNTUUSER,gid=UBUNTUGROUP,dir_mode=0770,file_mode=0770 0 0
```

Make sure VENUSUSER/VENUSPASS is the username and password for the venus system's shared drive. Make sure UBUNTUUSER/UBUNTUGROUP is your local ubuntu username and groupname (normally the same as your username).

4. Make sure there is one or more blank lines (press enter a few times) at the end of your fstab. Click CTRL+O then enter to save, then CTRL+X to quit.

5. Test your mount ...

```
sudo mount -a
```

If this works, it'll work automatically every time you start the computer.

Cheers
Callan

---

### Post by simartem on 2009-12-03
thanks for the helps.. i'll try them when i'm back home

---

### Post by WallaceTech on 2010-01-30
Hello. I have followed your notes and i can see my drive after i reboot my machine.

But when i try to open it, it informs me that only root can mount it.

Any ideas, Ubuntu and Linux is very new to me

Thanks in advance


> **callan79 said:**
> Hi simartem,

You should probably have a look at [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently), but to give you a quick overview ...


1. Make a new mount point :

```
sudo mkdir /media/venus
```2. Open your fstab file so you can add the mount details

```
sudo nano /etc/fstab
```3. Add the following line to the end of fstab :

```
//192.168.5.23/hdd1/ /media/venus cifs auto,nounix,noserverino,user=VENUSUSER,password=VENUSPASS,uid=UBUNTUUSER,gid=UBUNTUGROUP,dir_mode=0770,file_mode=0770 0 0
```Make sure VENUSUSER/VENUSPASS is the username and password for the venus system's shared drive. Make sure UBUNTUUSER/UBUNTUGROUP is your local ubuntu username and groupname (normally the same as your username).

4. Make sure there is one or more blank lines (press enter a few times) at the end of your fstab. Click CTRL+O then enter to save, then CTRL+X to quit.

5. Test your mount ...

```
sudo mount -a
```If this works, it'll work automatically every time you start the computer.

Cheers
Callan

---

### Post by quixote on 2011-02-15
To make the drive mountable by non-root users, change the uid and gid options in the fstab line:```
uid=1000,gid=1000
```That's what callan79 was talking about with "uid=UBUNTUUSER" "gid=UBUNTUUSER".  callan79 is suggesting using your login name, but I've always seen it done numerically.  This way all non-root users on the machine can mount the drive, plus it seems to work more consistently than using login name.

---

