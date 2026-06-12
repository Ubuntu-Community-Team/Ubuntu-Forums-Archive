---
title: "BROKEN: Nothing but blank screen and cursor on startup. Please help!"
date: 2009-08-27
forum: General Help
---

### Post by Danoz on 2009-08-27
I have been troubleshooting this for some time to no avail. I've been using Ubuntu for over a year now on my Sony Vaio. I am using Jaunty Jackalope and, to date, everything has worked just fine. When I turn on my computer everything comes up (I choose my top Ubuntu partition) and then the loading screen comes up-- then I am greeted with a black screen and a white cursor (the mouse works). I can access a command line interface as well and I've run just about everything there is to run in recovery mode. No help. Here's a list of things I've done so far:

- Tried logging and and stopping and starting the GNOME session using "sudo /etc/init.d/gdm stop" and "startx /usr/bin/gnome-session." This just takes me back to the same black screen.

- Tried to completely remove and reinstall the ubuntu desktop and ran all possible updates and upgrades from the command line.

- Tried to reconfigure the server using sudo dpkg-reconfigure xserver-xorg

Occasionally, when I try to restart the gnome desktop it takes me to the screen (after a minute of waiting) but the colors are completely destroyed (hyper-saturated, loaded with errors, text does not display properly etc. etc.)-- returning to the command line brings back dozens of errors. I'm worried that by reconfiguring everything I've made things worse... it took some time get Ubuntu and my Sony Vaio playing nice. Right now I am back to the black screen of death.

Please help!! What else can I do? Worst case I may need to recover my files from the Vista partition and do a fresh install (gaaaah!) but I wouldn't even know how to do that without messing up my Vista side.

---

### Post by Danoz on 2009-08-27
Please don't let this get buried. This is a really disconcerting problem and I would very much like to have use of my laptop again... at this point I wouldn't be opposed to a fresh install as long as I could be sure that Vista partition wouldn't be injured by whatever actions I take here. Feel free to contact me by AIM instant messenger (danoz2k8) if you think you can help.

---

### Post by karlmp on 2009-08-27
is easy and fast to do a fresh install just choose manual partition when in the process of install

---

### Post by NoaHall on 2009-08-27
okay, what have you installed/changed recently? what kind of graphics card do you have?

---

### Post by Danoz on 2009-08-27
> **NoaHall said:**
> okay, what have you installed/changed recently? what kind of graphics card do you have?

Nvidia GeForge Go 7200 -- I did have to play around in order to get this working correctly when I first installed Ubuntu last year (had problems getting wireless to work also)-- but I've had no problems with it (I can even run Compiz effects easily and run Wings3D).

I can't think of anything I've installed recently that could be the cause-- but I DID have to do a hard restart after the computer froze at startup... ever since it seems that something has gone very wrong. If I can avoid having to reinstall I would like to... my first install took hours of tinkering and it threw Vista out of whack.

Additional specs:
Sony Vaio VGN-SZ430N - 2 GB RAM - Intel Core 2 CPU T7200 @ 2.00Ghz - Nvidia GeForge Go 7200

---

### Post by NoaHall on 2009-08-27
If you still have the disk - boot up with the disk in, see if loads fine. If it does, do "sudo fsck" on the disk you use as "/"

---

### Post by Danoz on 2009-08-27
Boots up fine from the disk as a temporary session. Not quite sure how to use the fsck command-- but I can "mount" the volumes from either partition. Who command should I put in from terminal when booted from CD?

---

### Post by P4man on 2009-08-27
attach you xorg logfile. From the live cd, open nautilus (file browser) and locate this file:

/media/yourharddisk/var/log/Xorg.0.log

attach to a post here so we can have a look.

[SIZE="1"]btw, 1 hour post bumping is considered rude, and private help (pm or msn or whetever) is only given when you pay for it :) The advantage of a public forum is that everyone can benefit and contribute. [/SIZE]

---

### Post by NoaHall on 2009-08-27
You don't want to mount to use fsck. 

"sudo fsck -F#filetype here# #location of hd here#"

Well, okay, do cat /etc/mtab and cat /etc/fstab first and post here what you get

---

### Post by Danoz on 2009-08-27
I have located and attached this file as requested (had to compress to upload). Tried using fsck but I think I'm doing something wrong... it's not entirely clear to me how to write the drive location. I do know that 

ubuntu@ubuntu:~$ sudo fsck -f /etc/fstab
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /etc/fstab
Could this be a zero-length partition?

Here is some information about the drive where my ubuntu partition is located:

Mount Point: /media/disk
File System: ext3

---

### Post by NoaHall on 2009-08-27
no, I meant, just do "cat /etc/mtab" and "cat /etc/fstab" and post the result

---

### Post by P4man on 2009-08-27
fsck is to be run on a partition,  not a file (/etc/fstab is just a file).

```
fsck /dev/<your partition>
```

Partition would be like /dev/sda1

If you are not sure which partition you can use:

```
sudo fdisk -l
```

to help you find it.

As for the xorg log file. Are you sure that is the log file from your harddisk and not from the live session? It certainly doesnt load the restricted binary drivers, it runs the opensource "nv" driver. I think you browsed to 
/var/log/...
and not
/media/yourdisk/var/log/...

---

### Post by Danoz on 2009-08-27
You are 100% correct I posted the wrong file. Here is the correct version from my mounted volume.

EDIT: figured fsck out.. here's the output:

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 243189/2199344 files, 4059244/8791563 blocks
ubuntu@ubuntu:~$ 


something I'm doing wrong here? Attached is newer version of Xorg log file. Anything else you guys need?

---

### Post by P4man on 2009-08-27
> **Danoz said:**
> 

ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 243189/2199344 files, 4059244/8791563 blocks
ubuntu@ubuntu:~$ 

Try forcing the check:

```
 sudo fsck **-f /**dev/sda5
```

>  Attached is newer version of Xorg log file. 

Its newer, but its still from a session using the opensource "nv" driver. You sure you got the right one ? Where did you find it?

---

### Post by Danoz on 2009-08-27
The new xorg file is definitely the right one because it has "Serenity" (the name of my computer in the partition) in the document.

Forced the output on the fsck... here's what I got:

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda5
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 243189/2199344 files (1.8% non-contiguous), 4059306/8791563 blocks
ubuntu@ubuntu:~$


Still opening to a black screen but I don't think I've really changed anything yet.

---

### Post by NoaHall on 2009-08-27
At this point, I'd say just reinstall - unless you've done something you reallly shouldn't have, I can't think of anything.

---

### Post by P4man on 2009-08-27
well, its clearly loadiing the "nv" drivers. lets see what happens when you install the nvidia ones:

```
sudo apt-get install nvidia-glx-180
```

---

### Post by Danoz on 2009-08-27
> **P4man said:**
> well, its clearly loadiing the "nv" drivers. lets see what happens when you install the nvidia ones:

```
sudo apt-get install nvidia-glx-180
```

It says that that version is already installed. I'm at a loss here... I may as well reinstall but I'm a bit nervous in the partitioner of the live CD..... would anybody mind walking me through this so that I don't accidentially destroy my Vista partition? (lot of important software on that side)

---

### Post by P4man on 2009-08-28
Before reinstalling, Id try at least 2 more things. You may have the binaries installed, but X isnt using them. Run this to reconfigure X:

```
sudo nvidia-xconfig 
```

If that doesnt help, I would rename your home folder, and create a new one, so that you start will all default settings. You can later copy your files and settings you want from the renamed folder.

to do that:

```
sudo -i
cd /home
mv username username.backup
mkdir username
chown -R username:username /home/username
```

---

### Post by Danoz on 2009-08-28
Excellent!

That WORKED! :) :guitar:

Thanks for your help this is great! The computer has been restored to its default settings and it loads right away-- wireless and graphics card (and most of my custom configurations) are still in tact in functioning properly.

---

