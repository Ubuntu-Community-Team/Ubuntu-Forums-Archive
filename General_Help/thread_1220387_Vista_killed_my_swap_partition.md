---
title: "Vista killed my swap partition"
date: 2009-07-22
forum: General Help
---

### Post by mavis311 on 2009-07-22
I'm using vista and 8.10 Intrepid on my laptop.  I had these partitions set up (in this order):
Toshiba recovery : Vista Primary : Free Space : /home : Linux Swap : Ubuntu 8.10 OS

Under Vista (big mistake, apparently), I chose to split up my Free Space so that I might move my documents to part pf that space.  I had windows Disk Management (wDM) "create a simple partition" of 20G in that Free Space.  When it had finished, it created the 20G as a primary partition and my /home and linux swap partitions had been merged into a single chunk of "Free Space" according to wDM. :confused:

Ubuntu begins to boot, but abrutly stops and drops to a root shell.  That is a logged in as root shell "root@rigel# ".  I can "exit" the shell and gnome comes to the login screen.  After login, errors are generated until boot ceases.  I can still ctrl-alt-f1 to a terminal and can do stuff there.

I recreated a home dir in /home for my main login: mavis (ie-/home/mavis).  I chown'd /mavis for user mavis.  I know there are some files that need to go in there, but I think that perhaps linux is smart enough to generate them???  Should I just recreate my user stuff?

Not sure if that will work, or help, but I'm guessing I really need to recreate the swap partition.  I'm just afraid that if I mkswap /dev/???  I'm gonna need to wipe and reinstall both Vista and Ubuntu.

I guess I could just reinstall Intrepid and recreate my /home and swap parts like I did the first time, but I figure I'll learn more if I do it manually. :D

Any suggestions?

---

### Post by XCan on 2009-07-23
What is your output of

```
fdisk -l
```

and

```
df -h
```

I would say that if indeed your swap partition is gone, you should use a partition manager, gparted, for example, to first create the partition before trying some ninja stunts.

---

### Post by mavis311 on 2009-07-23
> **XCan said:**
> What is your output of

```
fdisk -l
```and

```
df -h
```I would say that if indeed your swap partition is gone, you should use a partition manager, gparted, for example, to first create the partition before trying some ninja stunts.

here is the requested output, meticulously recreated from screen shots (i.e.-photos):
```
root@rigel:~# fidsk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38dda024

Device     Boot     Start        End      Blocks    Id  System
/dev/sda1               1        192     1536000    27  Unknown
/dev/sda2    *        192       6719    52429812     7  HPFS/NTFS
/dev/sda3           17859      24321    51914047+    5  Extended
/dev/sda5           20857      24321    30001387+   83  Linux


root@rigel:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              29G  3.4G   24G  13% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  4.0K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  3.1M  945M   1% /dev
tmpfs                 948M     0  948M   0% /dev/shm
lrm                   948M  2.2M  946M   1% /lib/modules/2.6.27-12-generic/volatile

```That /dev/sda3 is my /home and swap partitions.  Well, it used to be those partitions anyway.

---

### Post by XCan on 2009-07-23
I just want to start with that I am no expert in this. But have you tried to mount the extended partition (I would be it won't work but could try anyway), and what happens when you look at it from gparted? 

Regarding your first question about which files needed to be 'auto created' in your home directory, Ubuntu would not do it just because you created a new dir in your /home. However, if you add a new user through CLI 'adduser' or using the GUI manager in System, Ubuntu will create the standard settings files, which you then could copy over to your current user.

---

### Post by mavis311 on 2009-07-23
> **XCan said:**
> I just want to start with that I am no expert in this. But have you tried to mount the extended partition (I would be it won't work but could try anyway), and what happens when you look at it from gparted? 

Regarding your first question about which files needed to be 'auto created' in your home directory, Ubuntu would not do it just because you created a new dir in your /home. However, if you add a new user through CLI 'adduser' or using the GUI manager in System, Ubuntu will create the standard settings files, which you then could copy over to your current user.


Well, no I haven't tried to mount the partition.  I don't really know how to do that at the terminal.  I'll see what I can do... gparted shows the same stuff that fdisk shows and that wDM shows: a logical partition that it considers to be 20G of "free space."  

I didn't think wDM would do this to me.  Guess that's what I get for not knowing what a "simple volume" actually is.  I'm not sure, but I believe that windows changed the partition that contained my linux swap into a dynamic volume, or maybe it already was dynamnic.  At any rate it's not the way it used to be.

Yeah, I didn't think that linux would "auto create" any files just because I created a dir in the /home dir.  I had hoped that logging in as that user might generate a state which would cause linux to create the default user files in that user's home dir.  I'll look up this CLI 'adduser' to see what that can do.  However, gnome still doesn't boot properly and I don't believe it will until I can recreate a swap partition.  Maybe not even then, but I've heard of some effed up linux/unix systems still being able to run and be repairable after worse than what has happened to my drive.

I wish I had stuck with RedHat back in the day.  X never would run on my machine, I don't think it liked the Diamond video card I was using back then.  If only I had stuck with the terminal only functionality that it had, I'd be much more knowledgable about doing stuff at the command line.  At least I can still learn it.

---

### Post by mavis311 on 2009-07-26
This situation has been obsoleted due to my inability to rescue my ubuntu install.  I was unable to mount the partition, whether due to my lack of experience with linux or another problem with the partition in question, I can't say.  I was also unable to create any new users.  While logged in as root, I would get error messages stating that I could not create a user due to my insufficient privilege level or something like that.  

At any rate, I used BootItNG to delete all partitions on my drive excepting my Vista partition and the "restore" partition and restore the MBR.  Vista booted up perfectly afterwards with none of the problems I expected to have at boot up.  I simply shutdown after discovering this and reinstalled 8.10 and recreated my partition setup at the same time.  Problem solved, I guess.  Unfortunately, I learned none of the things I had hoped to learn about linux from this mishap.  I did, however, learn that the windows Disk Manager is of very little use to me now that I have linux installed.

---

