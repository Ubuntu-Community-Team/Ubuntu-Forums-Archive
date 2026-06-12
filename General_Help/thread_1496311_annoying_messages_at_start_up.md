---
title: "annoying messages at start up"
date: 2010-05-29
forum: General Help
---

### Post by siyfound on 2010-05-29
HI all, this is my first post so please bear with me! been using linux on and off for a while now but when built my new computer it has become my permanent os of choice, so would like to sort out a few niggles. 
i have 3 hard drives installed originally one was for the os and the other 2 were still ntfs as they had movies and stuff on anyway i got it all sorted so they would mount at boot etc.
But i formatted them the other day and renamed etc. but on bootup it comes up with a message saying 

could not find "media/MORE_MOVIES"

that was the name of one of the hard drives before i formatted and renamed.but i cannot get rid of this message. have dug into fstab etc and i cannot find a reference of this anywhere so what is producing this notice?

Any help would be greatly appreciated. please be aware i am so so with linux so nothing to complicated!cheers

---

### Post by lmarmisa on 2010-05-29
Check the contents of the /etc/fstab file.

Type the command:

> 
cat /etc/fstab


---

### Post by inso_741 on 2010-05-29
post /etc/fstab here

---

### Post by siyfound on 2010-05-30
> **lmarmisa said:**
> Check the contents of the /etc/fstab file.

Type the command:


HI sorry about the delay, thought it would auto subscribe to my own thread but i guess not, here is the fstab file you asked for


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc            proc  nodev,noexec,nosuid  0  0  
#Entry for /dev/sdb1 :
UUID=6d8124aa-ba85-4261-86ec-124bfe975a8b  /                ext4  errors=remount-ro    0  1  
#Entry for /dev/sdb5 :
UUID=def7c936-2c05-4b19-a09c-9c60cc040e5d  none             swap  sw                   0  0  
/dev/sdb1	/media/hdd2 	ext4	defaults	0 2
/dev/sdc1	/media/hdd1     ext4    defaults        0 2

---

### Post by lmarmisa on 2010-05-30
Could you type these commands too?

```

sudo blkid

ls -l /media

```

---

### Post by siyfound on 2010-05-30
first command

/dev/sda1: UUID="6d8124aa-ba85-4261-86ec-124bfe975a8b" TYPE="ext4" 
/dev/sda5: UUID="def7c936-2c05-4b19-a09c-9c60cc040e5d" TYPE="swap" 
/dev/sdb1: LABEL="hdd2" UUID="0cea4142-e948-4c08-93a0-c1265843adc0" TYPE="ext4" 
/dev/sdc1: LABEL="hdd1" UUID="76258325-4c77-4617-87b6-23739ce56f88" TYPE="ext4"

second command

total 8
drwx------ 6 simon simon 4096 2010-05-30 09:13 hdd1
drwx------ 3 simon simon 4096 2010-05-06 16:19 hdd2


thanks for replying so fast, am off to bed now need some rest.i will come back online and check in morning.thanks very much for helping me so far.

---

### Post by lmarmisa on 2010-05-30
A new command, please:

> 
cat /etc/mtab


---

### Post by siyfound on 2010-05-31
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb1 /media/hdd2 ext4 rw 0 0
/dev/sdc1 /media/hdd1 ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/simon/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=simon 0 0

---

### Post by arrange on 2010-05-31
Could you post a screenshot of the message? It doesn't seem to be coming from *mountall*...

---

### Post by siyfound on 2010-05-31
[IMG]http://i720.photobucket.com/albums/ww207/siyfound/error.png[/IMG]

---

### Post by dino99 on 2010-05-31
install: locate

then into console: locate media/MORE_MOVIES

if this folder/file dont exist or is empty, erase it

sudo dpkg --configure -a

mountmanager is a usefull tool to deal with partitions and devices

---

### Post by lmarmisa on 2010-05-31
I have found this Nautilus bug report that could be related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/385113](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/385113)

In any case, did you define any launcher or Nautilus reference pointing to the old directory /media/MORE_MOVIES?.

Maybe have one of the Startup Applications defined a pointer to the old hard drive?. Perhaps the Bluetooth Manager?. This is only an idea.

---

### Post by siyfound on 2010-05-31
> **dino99 said:**
> install: locate

then into console: locate media/MORE_MOVIES

if this folder/file dont exist or is empty, erase it

sudo dpkg --configure -a

mountmanager is a usefull tool to deal with partitions and devices


Hi, tried the locate and it came back with nothing? very weird. its not the end of the world or anything would just like to stop it showing up each time. will have a go at mountmanager in a moment.cheers

---

### Post by siyfound on 2010-05-31
> **lmarmisa said:**
> I have found this Nautilus bug report that could be related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/385113](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/385113)

In any case, did you define any launcher or Nautilus reference pointing to the old directory /media/MORE_MOVIES?.

Maybe have one of the Startup Applications defined a pointer to the old hard drive?. Perhaps the Bluetooth Manager?. This is only an idea.

quite possibly i did, the drives were originally ntfs so i used ntfs-config tool? but i removed it.

---

### Post by lmarmisa on 2010-05-31
Try to create the old directory and check if the error message changes:

> 
sudo mkdir /media/MORE_MOVIES
sudo chmod 777 /media/MORE_MOVIES


---

### Post by siyfound on 2010-05-31
> **lmarmisa said:**
> Try to create the old directory and check if the error message changes:

Aha!! done the above and now it opens the file browser to that folder, no more error messages. so i guess something is trying to mount this folder all the time. now just have to find what is. any ideas?

---

### Post by lmarmisa on 2010-05-31
I believe that this is not a problem related to a mount attempt.

This seems a program started by Nautilus at the beginning of your session pointing to the old hard drive. Check the candidates clicking on System -> Preferences -> Startup Applications.

---

### Post by siyfound on 2010-05-31
> **lmarmisa said:**
> I believe that this is not a problem related to a mount attempt.

This seems a program started by Nautilus at the beginning of your session pointing to the old hard drive. Check the candidates clicking on System -> Preferences -> Startup Applications.

just had a look around in there, nothing seems to be out of the ordinary.here is what i have

[IMG]http://i720.photobucket.com/albums/ww207/siyfound/startupapps.png[/IMG]

[IMG]http://i720.photobucket.com/albums/ww207/siyfound/startupapps2.png[/IMG]

---

### Post by lmarmisa on 2010-05-31
Is PS3 Media Center trying to serve videos located in the old hard drive?. Personal File Sharing?. Even Bluetooth?.

Untick temporarily the suspicious programs and try to identify who is guilty.

---

### Post by siyfound on 2010-05-31
> **lmarmisa said:**
> Is PS3 Media Center trying to serve videos located in the old hard drive?. Personal File Sharing?. Even Bluetooth?.

Untick temporarily the suspicious programs and try to identify who is guilty.

I'm on it, will report back shortly!!

---

### Post by adarsh_iitg on 2010-05-31
I have a problem, solution to which I could not find anywhere. 

here it goes:

My ubuntu 10.04 64-bit was running extremely well. I tried to install a few packages for google-gadgets from the offical website. it was unsuccessful.
adding to it, my login screen has disappeared. After booting, only the background screen(theme) comes without any login window. absolutely nothing is written ...

please help me. I tried recovery option from the grub menu, but could not find anything relevant (like system restore to factory settings or similar) 

however I can reach command line login by pressing ctrl+alt+f2 and hence login into command line environment ....

Can anything be done from the terminal ???please suggest ....

---

### Post by siyfound on 2010-05-31
> **siyfound said:**
> I'm on it, will report back shortly!!

unticked all you can see and still get it, this is very confusing

[IMG]http://i720.photobucket.com/albums/ww207/siyfound/stillfailed.png[/IMG]

---

### Post by siyfound on 2010-05-31
don't dare untick anymore unless it nevers starts up again!!

---

### Post by lmarmisa on 2010-05-31
You know now the startup apps are innocent.

The problem seems j*#i[]o! (censored).  :)

Did you remove the /media/MORE_MOVIES directory?.

---

### Post by siyfound on 2010-05-31
> **lmarmisa said:**
> You know now the startup apps are innocent.

The problem seems j*#i[]o! (censored).  :)

Did you remove the /media/MORE_MOVIES directory?.

yep, removed the folder by

sudo rmdir /media/MORE_MOVIES

thanks for all your help, guess i will have to keep digging about and see what i can find out. right off for some dinner.:popcorn:

---

### Post by inso_741 on 2010-05-31
What happens when you create the folder again?

---

### Post by siyfound on 2010-05-31
> **inso_741 said:**
> What happens when you create the folder again?

it just opens the folder at login instead of giving the error

---

### Post by inso_741 on 2010-05-31
try this in your fstab
```
proc /proc proc nodev,noexec,nosuid 0 0 
#Entry for /dev/sdb1 :
UUID=6d8124aa-ba85-4261-86ec-124bfe975a8b / ext4 errors=remount-ro 0 1 
#Entry for /dev/sdb5 :
UUID=def7c936-2c05-4b19-a09c-9c60cc040e5d none swap sw 0 0 
#/dev/sdb1	/media/hdd2 ext4	defaults	0 2
#/dev/sdc1	/media/hdd1 ext4 defaults 0 2
```

---

### Post by siyfound on 2010-05-31
opened fstab, copy and pasted it across, saved it and logged out and logged in. no change?

---

### Post by arrange on 2010-05-31
This will take a while, but might be able to find a reference to the folder in a config file, try it```
grep -lIR MORE_MOVIES /etc ~ 2> /dev/null
```

---

### Post by inso_741 on 2010-05-31
try this in your fstab
```
proc /proc proc nodev,noexec,nosuid 0 0 
#Entry for /dev/sdb1 :
UUID=6d8124aa-ba85-4261-86ec-124bfe975a8b / ext4 errors=remount-ro 0 1 
#Entry for /dev/sdb5 :
UUID=def7c936-2c05-4b19-a09c-9c60cc040e5d none swap sw 0 0 
/dev/sdb1	/media/MORE_MOVIES ext4	defaults	0 2
/dev/sdc1	/media/MORE_MOVIES ext4 defaults 0 2
```

try puting a # before either of them

---

### Post by siyfound on 2010-05-31
> **inso_741 said:**
> try this in your fstab
```
proc /proc proc nodev,noexec,nosuid 0 0 
#Entry for /dev/sdb1 :
UUID=6d8124aa-ba85-4261-86ec-124bfe975a8b / ext4 errors=remount-ro 0 1 
#Entry for /dev/sdb5 :
UUID=def7c936-2c05-4b19-a09c-9c60cc040e5d none swap sw 0 0 
/dev/sdb1	/media/MORE_MOVIES ext4	defaults	0 2
/dev/sdc1	/media/MORE_MOVIES ext4 defaults 0 2
```

try puting a # before either of them


did what you said earlier, here is the file as it is now


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc nodev,noexec,nosuid 0 0 
#Entry for /dev/sdb1 :
UUID=6d8124aa-ba85-4261-86ec-124bfe975a8b / ext4 errors=remount-ro 0 1 
#Entry for /dev/sdb5 :
UUID=def7c936-2c05-4b19-a09c-9c60cc040e5d none swap sw 0 0 
#/dev/sdb1	/media/hdd2 ext4	defaults	0 2
#/dev/sdc1	/media/hdd1 ext4 defaults 0 2


what do the #'s do? like i said it still brings up the error

---

### Post by siyfound on 2010-05-31
sorry just saw your editing, will try now

---

### Post by siyfound on 2010-05-31
tried it with the MORE_MOVIES prefix in fstab no change?

---

### Post by inso_741 on 2010-05-31
did you remove the # ?
#'s make the lines to be ignored as comments

---

### Post by siyfound on 2010-05-31
> **inso_741 said:**
> did you remove the # ?
#'s make the lines to be ignored as comments

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0 
#Entry for /dev/sdb1 :
UUID=6d8124aa-ba85-4261-86ec-124bfe975a8b / ext4 errors=remount-ro 0 1 
#Entry for /dev/sdb5 :
UUID=def7c936-2c05-4b19-a09c-9c60cc040e5d none swap sw 0 0 
/dev/sdb1	/media/hdd2 ext4	defaults	0 2
/dev/sdc1	/media/hdd1 ext4 defaults 0 2


this is how it is now

---

