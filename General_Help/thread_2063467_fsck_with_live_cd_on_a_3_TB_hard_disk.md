---
title: "fsck with live cd on a 3 TB hard disk"
date: 2012-09-27
forum: General Help
---

### Post by ELMIT on 2012-09-27
.. it is the things you hardly need daily, ...


I got some errors on my 3 TB hard disk and want to run a checkdisk.

I cannot figure out how to do it correct.

I tried to boot the live CD (12.04.1 - amd64) and opened a terminal. There I typed in:

sudo fsck /dev/sda1

It responds:

fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superbllock invalid, trying backup blocks....
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda1

....


How do I need to do it???

---

### Post by HiImTye on 2012-09-27
what file system is it on the drive?

---

### Post by shreepads on 2012-09-27
Paste output from parted -l

---

### Post by ELMIT on 2012-09-27
I guess it is ext4  

parted -l   
Error: Can't have a partition outside the disk!

---

### Post by westie457 on 2012-09-27
> **ELMIT said:**
> I guess it is ext4  

parted -l   
Error: Can't have a partition outside the disk!

Depending on the type of partition table on the drive (MBR or GPT) one of these links will help you.

[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

A 3TB drive in all probability will have a GPT partition table though TBH am not sure so both links posted.

Read through before committing to anything.

---

### Post by ELMIT on 2012-09-27
thanks for the links, but I do not understand what I am looking for on that pages.

---

### Post by westie457 on 2012-09-27
Somehow the partition table has corrupted which has caused the message 'you cannot have a partition outside the disk' error.

'Fixparts' should repair this automagically however if used on the wrong type of partition table it will convert the drive to a GPT table.

A different thing to try is testdisk. More information and tutorials here 

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

Again read through things before committing.

Testdisk will only make changes when you tell it to and has more options for checking what you have.

Hope this helps.

---

### Post by ELMIT on 2012-09-27
sory, I made mistake ;-)

sudo parted -l   

Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/as: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system   Name  Flags
 1      17.4kB  1018kB  1000kB                      bios_grub
 2      1018kB  2983GB  2983GB  ext4
 3      2983GB  3001GB  17.2GB  linux-swap(v1)

---

### Post by westie457 on 2012-09-27
No worries, so did I by not noticing that parted -l needs sudo. The same as fdisk -l

I usually check drives for errors using Gparted or Disk Utility from a LiveCD, mainly because my grasp of command in the terminal is next to non-existent.

---

### Post by shreepads on 2012-09-27
Your ext4 partition is the **second **one on the disk so you need to run

```

sudo fsck /dev/sda2

```

and not

```

sudo fsck /dev/sda1

```


To force a full scan for bad blocks:

```

sudo e2fsck -cf /dev/sda2

```

Note, for a 3TB drive this may take ~ 7.5 hrs...

---

### Post by ELMIT on 2012-09-27
thank you very much. Now the full check is running. 

I am aware that it will take a long time, I am happy that it starts now and I can use my computer hopefully tomorrow again, ...

Will report when finished!

Thanks again.

---

### Post by ELMIT on 2012-09-27
when I came back, the screen showed:

ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda2: clean, 24081073/182099968 files, 536479695/728372558 blocks
ubuntu@ubuntu:~$ sudo e2fsck -cf /dev/sda2
e2fsck 1.42 (29-Nov-2011)
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                
/dev/sda2: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 24081073/182099968 files (0.1% non-contiguous), 536479695/728372558 blocks


restart of the system, removing the live CD resulted in a black screen.
(first grub, then the usually white screen which goes black - and next should be the login) 

What  can I do next?

---

### Post by ELMIT on 2012-09-27
I tried a couple of things:
press the power button, which shuts down the machine

reboot into recovery mode. Goto root shell and looked around, ... nothing to see.

typed in the shutdown command.


started again, ... 

this time the screen stopped at the first red dot of the picture: 
[CENTER]Ubuntu 12.04 
. . . . 
[/CENTER]

switch to another console let me login 

dmesg last lines are:

[37.99775] init: plymouth-stop pre-start process (6034) terminated with status 1
[44.672061] init: failsafe-x main process (2538) terminated with status 1


boot.log ends with the line:
* Starting LightDM Display Manager     [OK]


startx gets me into it now (since I was already logged in at text mode, no login screen)

Any ideas how to fix that?

---

### Post by ELMIT on 2012-09-27
while graphic appeared, Unity failed to start, .... and so the screen was useless.

I went back to ALT-F2 and found the last line showing:
Parse error on line 128 of section Files in file /etc/X11/xorg.conf
   Ignoring obolete keyword "RgbPath".

ALT-F1, ALT-F3, ... show me login prompts

ALT-F7 shows me the Ubuntu 12.04 / .... 
ALT-F8 shows me the graphic screen without Unity


What to try next???

---

### Post by Bashing-om on 2012-09-27
elmit;

after you login from terminal...what is the result of:
```
sudo service lightdm start
```as of unity the service is changed from using "startx" .
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by ELMIT on 2012-09-27
I tried: > sudo service lightdm start

and it resulted in exactly the same screen

[CENTER]Ubuntu 12.04
. . . .
[/CENTER]
with the first dot in red and stops there!

> as of unity the service is changed from using "startx" .

    hth <==BDQ

I have no idea what it means for me.

---

### Post by ELMIT on 2012-09-28
In the meantime some upgrades came in, ...(I thought maybe that fixes, ...)


If I reboot I come to the picture as attached. 

I can only go to my system if I boot in recovery mode, and then continue. Then it stucks at the Ubuntu screen, but it let me switch to another console (ALT-F2) and startx which comes to the graphic screen. Unity I get by opening a terminal and 
unity --reset


How can I get my system back????

---

