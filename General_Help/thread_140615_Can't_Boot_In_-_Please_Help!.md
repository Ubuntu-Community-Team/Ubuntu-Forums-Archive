---
title: "Can't Boot In - Please Help!"
date: 2006-03-06
forum: General Help
---

### Post by Ingla on 2006-03-06
Hello.

I've posted some of this before, but haven't found anyone online who could help. If anyone knows about these things, I'd appreciate assistance.

I've been running Ubuntu 5.10 (Breezy) for a while with no special
problems. It's on a separate hard drive in a removable drawer. I'm not
talking about USB or other removable media. A computer has room and
cables for two hard drives (at least). The drawers, which I've been
using for years, simply plug in to the cables. The frame of the drawer
is permanently connected to the cables leading to the motherboard. The
removable part simply plugs in with pins to the frame. That way, you
can remove one hard drive and put in another without opening the
machine. However, this is exactly the same as if you did open it and
change the hard drives.

The Linux disk had been out of the machine for about 24 hours. It had
been working fine and I had made no recent installations or other changes.

When I put in the disk and tried to boot into Ubuntu as usual, I got this:

Alert! /dev/hdc1 does not exist. Dropping to shell!

It just hung on that.

After going to Windows and coming back, I got the same thing several
times. Once, it continued, saying:

BusyBox v1.00-pre10 (Debian 20040623-1ubuntu 22) Built in shell (ash).
Enter 'help' for a list of built in commands.
/bin/sh: can't access tty: job control turned off
#_

Usually, it doesn't get that far, but just hangs on the first message.

Can anyone tell me how such a thing could happen and what - if
anything - I can do about it?

Someone suggested this may have been caused by removing a hard disk
before it was unmounted. I've never done that. I only change hard
drives after going out of Linux (or Windows) in the proper manner and
after the machine is turned off. However, I have some reason to
suspect that another user on this machine is not quite so careful.
It's not impossible that he hit "Shut Down" and immediately pulled the
hard drive.

In any case, I've heard this may be fixable (I've spent a lot of time
and effort setting up this system and it would be a shame to have to
format and start again...especially since I can't even get in to copy
out all the how-to's I had been compiling in case I needed to retrace
my steps).

Under Windows, I would have a good idea where to start to attempt a
fix (although, if Windows breaks, it's often hopeless). At minimum,
I'd have a good chance of recovering data. But, I'm a Linux
newbie...at least as far as anything like this is concerned. 

I do have an Ubuntu Live CD, but have never tried to use it (hope it
boots). I've heard about fsck, but it has a lot of optional parameters
and, if I understand correctly, I have to be sure that no part of the
Linux system is mounted, or I could kill it for good.

What I need is a one-step-at-a-time walk-through, in baby talk. If
anyone knows how to go about this, I'd certainly appreciate the help.

Thanks very much.

---

### Post by dcstar on 2006-03-07
[QUOTE=Ingla]
......
When I put in the disk and tried to boot into Ubuntu as usual, I got this:

Alert! /dev/hdc1 does not exist. Dropping to shell!
......
What I need is a one-step-at-a-time walk-through, in baby talk. If
anyone knows how to go about this, I'd certainly appreciate the help.

Thanks very much.[/QUOTE]
Ubuntu labels devices in the following way:

Master IDE device on first **detected** IDE channel: hda, Slave device : hdb

Master IDE device on second **detected** IDE channel: hdc, Slave device: hdd

If you drives are not detected in your BIOS exactly the same as before you changed things, then the Grub entries will not line up with the hardware it expects.

Your "hdc1" message means that Grub is looking for Ubuntu in Partition 1 on a Master IDE drive connected to you second IDE channel. Boot up your PC, go into the BIOS and make sure that the disk is detected ok in that place.

---

### Post by Ingla on 2006-03-07
Thanks for the reply.

I don't have the Linux disk in the machine at the moment, but there is a Windows backup disk in the 2nd IDE. It is recognized fine. There's no reason the Linux disk shouldn't be recognized in the same position (I'll double check anyway). The fact is GRUB starts to load before I get the error message, so it can't be that CMOS isn't finding the drive.

I haven't changed anything, including the order of IDE devices in the machine. As mentioned, this seems to have been caused by an improper shutdown. Something seems to have become corrupted in Ubuntu.

Any ideas?

Thanks.

---

### Post by syg00 on 2006-03-07
When in doubt boot Knoppix. See if it will find the drive - that way you can look at the loader and fstab.

---

### Post by Ingla on 2006-03-07
Thanks.

Remember, however, that I'm pretty new to Linux. I don't know what Knoppix is or how to boot it. I also don't know how to interpret whatever output I get.

Can you explain?

---

### Post by justleen on 2006-03-07
[QUOTE=syg00]When in doubt boot Knoppix. See if it will find the drive - that way you can look at the loader and fstab.[/QUOTE]


.. and perhaps a fdisk -l  to chekc the partition table

---

### Post by justleen on 2006-03-07
Knoppix is a live-boot linux enviroment - it runs from cd, just like the Ubuntu live cd option (not sure why knoppix would be different from Ubuntu-live cd though.. i would try to boot ubuntu live before getting knoppix), simply boot from the ubuntu cd and press Enter to load the live cd.

Once booted up you can list the partitions with **fdisk -l** 
the outpput should look like this 
```

	$ fdisk -l /dev/hda
	
	Disk /dev/hda: 15 heads, 57 sectors, 790 cylinders
	Units = cylinders of 855 * 512 bytes
	
	   Device Boot  Begin   Start     End  Blocks   Id  System
	/dev/hda1           1       1      24   10231+  82  Linux swap
	/dev/hda2          25      25      48   10260   83  Linux native
	/dev/hda3          49      49     408  153900   83  Linux native
	/dev/hda4         409     409     790  163305    5  Extended
	/dev/hdc1               409     744  143611+  83  NTFS
	/dev/hdc2         745     745     790   19636+  83  FAT32
	$

```
This will tell you what partition your Ubuntu is on 
have a look at /etc/fstab 
it should look something like this
```

/dev/hda2	/	ext2	defaults	1 1
/dev/hdb1	/home	ext2	defaults	1 2
/dev/cdrom	/media/cdrom	auto	ro,noauto,user,exe	0 0
/dev/fd0	/media/floppy	auto	rw,noauto,user,sync	0 0
proc	/proc	proc	defaults	0 0
/dev/hda1	swap	swap	pri=42	0 0

```
check wheter the right partitions are listed here (as shown in fdisk -l)
if not, edit it so it show the right partitions..

---

### Post by Ingla on 2006-03-07
Thank you very much.

I hope I can manage this. 

It will take a liitle while, so I hope I find some of you knowledgeable folks online when I get into the middle of this.

Meanwhile, a couple of preliminary questions:

1. Can I edit fstab from the Live CD, i.e., does it make me root?

2. Someone on another forum (who has since disappeared) told me to boot from Live CD with the Linux hard drive in place but nothing mounted, and to run fsck.
     a. If I boot from the CD, nothing is mounted...true or false? (this is      important because fsck running on a mounted file system could apparently kill it completely).
     b. Can fsck cure this automatically?
     c. fsck looks pretty complicated...lots of optional stuff, and I also found things like this:
-------------------------------------------------------------------------
Searching around, I found that fsck won't run if superblock is corrupted. This is the quote:
------------------------------------------------------------------
"If the superblock is corrupted the file system still can be repaired using alternate superblock which are formed while making new file system .

the first alternate superblock number is 32 and others superblock numbers can be found using the following command :

newfs -N /dev/rdsk/c0t0d0s6

for example to run fsck using first alternate superblock following command is used

fsck -F ufs -o b=32 /dev/rdsk/c0t0d0s6"
------------------------------------------------------------------
How would I know if I needed to do this? Can I do it from Live CD?
------------------------------------------------------------------
3. If I use the CD to run fdisk -l and need to edit fstab, how should I do that?

/dev/hdc1	/	ext3	defaults	1 1

If that's right, should it be the first entry? Is that the correct mount point?

Please advise.

Thanks very much.

---

### Post by syg00 on 2006-03-07
Sorry - Knoppix is the "grand-daddy" of liveCDs. Has _excellent_ hardware detection, and is very useful to keep handy for troubleshooting.
Ubuntu has a liveCD which may also do the job - never used it.

Boot Knoppix, get to a terminal session and do "fdisk -l" (ell for list), "cat /etc/fstab" and "cat /boot/grub/menu.lst"

*EDIT:* Got sidetracked half-way through composing - I see I was beaten to it.
LiveCDs run from the CD, so don't require the HD partitions - Knoppix for example mounts them all R/O to you can't do any damage.

As to your queries re fsck; I'd be just looking around for now - when you understand the situation, then you can think about fixing it.

---

### Post by justleen on 2006-03-07
[QUOTE=Ingla]

1. Can I edit fstab from the Live CD, i.e., does it make me root?
[/quote]
since your not loggin on to your own system, but booting another OS and mapping a drive you will be able to edit the file.
simple find your /etc/fstab, and edit it with vi or another editor

[QUOTE=Ingla]
     a. If I boot from the CD, nothing is mounted...true or false? (this is      important because fsck running on a mounted file system could apparently kill it completely).
[/quote] by default the drive should be mounted. you can simply check this with **mount -l** to see what is mounted. you can umount a drive with umount 
[QUOTE=Ingla]
     b. Can fsck cure this automatically?
[/QUOTE] it should be able, yes.. (if its a badblock somewhere, that is)
[QUOTE=Ingla]     c. fsck looks pretty complicated...lots of optional stuff, 
3. If I use the CD to run fdisk -l and need to edit fstab, how should I do that?
[/QUOTE] fsck simply checks fstab for the to scan, it should work with no option at all..

personally, i never unmounted any drives. fsck is just like CHKDSK, and it runs at boot as well.. cant really believe that it wil kill an HDD, though i can believe it will fsck-up your drive if it repairs a bunch of blocks.. (ever ran chkdsk on an old drive with bad blocks?)

[QUOTE=Ingla]
/dev/hdc1	/	ext3	defaults	1 1

If that's right, should it be the first entry? Is that the correct mount point?
[/QUOTe] Yep...
order doenst matter though

---

### Post by justleen on 2006-03-07
[QUOTE=syg00]
As to your queries re fsck; I'd be just looking around for now - when you understand the situation, then you can think about fixing it.[/QUOTE]

Syg00 is right on that one.. best to figure out if its simply some mess up in fstab/grub ...

---

### Post by Ingla on 2006-03-07
Hi.

I haven't actually done anything yet but research (and downloading Knoppix). Now I have that on a disk as well as Ubuntu's Live CD.

As I'm basically a cautious type, my plan is to follow syg00's initial advice and run:

fdisk -l 
cat /etc/fstab
cat /boot/grub/menu.lst

just to see what I can find out about what's going on. Then I'll try to get the outputs back here for you folks to examine, before I try anything.

I may have to take some round about measures to get the output in a form I can post here...OR...if I can connect while on the CD...maybe I can get back here while still in the process (if anybody's online). Otherwise, it's back and forth to and from Windows.

THE MAIN THING THAT'S BOTHERING ME (aside from the possibility that the system may not be fixable) is still running fsck on mounted partitions. Here are a couple of quotes from my research:
--------------------------------------------------------------------------
From LinuxQuestions forum:
If you have a liveCD to boot into, do so with the removable drive plugged in. 

Then try fsck on the removable drive. Do not mount it. Run fsck on unmounted 

partitions.
--------------------------------------------------------------------------
From [http://mail.nl.linux.org/linux-crypto/2003-06/msg00012.html](http://mail.nl.linux.org/linux-crypto/2003-06/msg00012.html)

Fsck'ing mounted partitions is not good idea. Read-only mounted root
partition gets fsck'ed at boot but that is special case.
--------------------------------------------------------------------------
From [http://www.gnoppix.org/pages/rute/node22.html](http://www.gnoppix.org/pages/rute/node22.html)
Note that you should not run fsck on a mounted file system. In exceptional 

circumstances it is permissible to run fsck on a file system that has been 

mounted read-only.
--------------------------------------------------------------------------
From:  [http://www.walterlamagna.com.ar/linux_disk_recovery.htm](http://www.walterlamagna.com.ar/linux_disk_recovery.htm)
The commands explained here can cause filesystem damage so i take no 

responsability for the results.
First use File System Check (fsck) to repair the filesystem, do not ever run fsck in 

a mounted partition, if you do so, fsck will warn you:

WARNING!!!  Running e2fsck on a mounted filesystem may cause

SEVERE filesystem damage.
-------------------------------------------------------------------------
From: [http://www.linuxhq.com/guides/SAG/x1038.html](http://www.linuxhq.com/guides/SAG/x1038.html)
fsck must only be run on unmounted filesystems, never on mounted filesystems 

(with the exception of the read-only root during startup). This is because it 

accesses the raw disk, and can therefore modify the filesystem without the 

operating system realizing it. There will  be trouble, if the operating system is 

confused.
-------------------------------------------------------------------------
There are some others, but I think you get the idea. I can't find the reference right now, but I saw somewhere that fsck can write some minor fixes to the root system EVEN THOUGH it's read only!

With all this is mind, I tend to think it would be much better to run fsck without anything mounted. Can you tell me how?

Thanks a lot.

---

### Post by justleen on 2006-03-08
that doenst matter that much really, just unmount the drive your gonna check. say, you want to fsck  /dev/hdc1. you can find in your fstab to where its mounted
**/dev/hdc2	/home	ext2	defaults	1 1**
then run **$ umount /home** to unmount the drive and **$ fsck /dev/hdc2**
You can add an -N flag to fsck to not execute, only show what is going to be done..

---

### Post by Ingla on 2006-03-08
Hello.

It looks like you guys are offline, so I hope you see this soon.

Here's the story:

I booted into Knoppix. It said it couldn't run the KDE interface because of insufficient memory. That's very strange because I'm running 512 (brand new chip), and have no problem running XP Pro with several heavy apps going at once. 

After I finished in Knoppix, I ran the Ubuntu Live CD, which had no problems.

I did have a terminal in Knoppix, which is the main thing.

The results don't look too happy. Here they are:
-------------------------------------------------------------------------
Knoppix:
-------------------------------------------------------------------------
fdisk -l   no output
- - - - - - - - - - - 
cat /etc/fstab
/proc     /proc     proc     defaults     00
/sys      /sys       sysfs    noauto      00
/dev/pts   /dev/pts  devpts  node=0626  00
/dev /fd0  /mnt/auto/floppy auto(?)   user,noauto, exec,ro  00
#Added by Knoppix
/dev/hdd1  /mnt/hdd1  ext3   noauto,users,exec   00
#Added by Knoppix
/dev/hdd5   none   swap   defaults  00
- - - - - - - - - - - -
cat /boot/grub/menu.lst
No such file or directory
--------------------------------------------------------------------------
Live CD
--------------------------------------------------------------------------
fdisk -l    No output
- - - - - - - - - - - - -
cat /etc/ fstab
/dev/mapper/casper-snapshot   /     auto   no???  00
tempfs    /temp    tempfs   nosuid,nodev     00
/dev/hdd5  swap    swap  defaults   00
- - - - - - - - - - - - -
cat /boot/grub/menu.lst
No such file or directory
--------------------------------------------------------------------------

As I had no way to copy/paste this stuff, I transcribed it by hand. ??? indicates where I had trouble reading my scribbling after I got back to Windows.

In any case, this gives me the impression of serious trouble. I'm not sure what it means except that my hard drives and boot menu don't exist. What else... who knows?

If I'm going to have to format and start from scratch, is there a way to get some of my how-to files off the disk? I don't seem to have access to the internet in Live CD (router admin indicates I'm connected, but can't access sites). I configured networking to static IP as it was in Ubuntu, but it didn't help. Ubuntu needed a reboot for that, if I recall, but I don't know whether Live CD saved my settings. What I mean is I don't know whether...if I can access my Home directory...I can e-mail files to myself or upload them (gftp had problems uploading in Ubuntu, so I used Krusader, but probably can't install it on Live CD).

Please let me know whether you think anything can be done about this and, if so, what and how.

Thanks very much.

---

### Post by virgule on 2006-03-08
I am sure dcstar is right. It must be just that --OR-- the drive is like..dead...  Lets see.. My point is to know if the drive is able to operate at all.. 

Please boot again a Live-CD (whichever one..) with the Linux drive connected and pipe dmesg to grep. Perhaps the Live-CDs are configured to ignore disks so they don't show up at all on fstab and friends.. Of course, if you can have both drives connected at once I am sure you could manage to figure it out from Windows.. but I am not a windude and I ain't talking Windows in here ;)

dmesg print out the kernel's bootup messages... This should tell us if the disk is seen or not by the kernel. Even a 'seen' drive does not automaticaly mean 'put in use' by the kernel.. Examine the output so you be able to recognize your Linux disk. We want to know WHERE the disk is connected( hda, hdb, hdc or hdd?!?) Then you will be able to adjust GRUB accordingly.

As exemple, on my box, running dmesg | grep hd output such lines among many others:
```

# dmesg | grep hd <enter>
hda: MATSHITA CR-585, ATAPI CD/DVD-ROM drive
hdc: WDC WD400BB-23JHA1, ATA DISK drive
SCSI device sdb: 17781520 512-byte hdwr sectors (9104 MB)
hda: ATAPI 24X CD-ROM drive, 128kB Cache
hdc: 78156288 sectors (40016 MB) w/2048KiB Cache, CHS=65535/16/63, (U)DMA

```
See it? I now know for sure 'hdc' is my HD and 'hda' is the cdrom.. Think of what dcstar said ;)
 
We might hit two birds with one stone here. We will see if the disk is there and where it is.

---

### Post by Ingla on 2006-03-08
Sounds reasonable.

I'm afraid it's more likely the drive is "dead", as you say, because nothing has been changed in the hardware cofiguration.

I'll give you plan a try.

I may also have another way to check what the configuration should be. I have a working Ubuntu disk, which was installed the same way this one was (it's just an old disk, making noises,etc. so I installed Ubuntu on a new disk as well).. If I recall, the drive is hdc1, the cd-rom is hdb and hda is the other IDE (whatever drive I have in it...if any. If you noticed, in the beginning of the post, Linux was looking for hdc1.

So, I'll run the test you suggest on the sick drive and maybe run the checks on the working drive to see what things ought to look like.

All this will take a little time, as I have to go offline and start changing disks, boot sequences, etc.

Thanks.

---

### Post by Ingla on 2006-03-08
Fortunately, I managed to get properly connected on the LIVE CD, and am writing from it now. This makes things a lot easier, as I can copy/paste the terminal output directly to the forum. At least something is working.

Here's the output:
-----------------------------------------------------------------------------------------------------------
ubuntu@mygateway:~$ dmesg | grep hd
    ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda : pio, hdb : DMA  <spaces inserted between ":" and adjacent letters to avoid smilies>
    ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc : pio, hdd : DMA <ditto>
hdb: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
hdd: SAMSUNG SP0411N, ATA DISK drive
hdd: max request size: 1024KiB
hdd: 78242976 sectors (40060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
hdd: cache flushes supported
hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Adding 1413680k swap on /dev/hdd5.  Priority:-1 extents:1
cdrom: hdb: mrw address space DMA selected
ubuntu@mygateway:~$
------------------------------------------------------------------------------------------------------
There's no disk in the bottom drawer (hda), which is how I usually boot into Linux. The disk called hdd here (Samsung) is the Ubuntu disk which is supposed to be booting. 

If you're still available, I'll wait here a few minutes to see if you want me to do anything else while I'm on the Live CD. Then I'll put in the old Ubuntu disk and see what things are supposed to look like.

Please let me know whether to do that now or do something else on Live CD.

Thanks.

---

### Post by virgule on 2006-03-08
I think we are done with Live-CD. We got what we need :)

Just point the bootloader (GRUB?) to hdd1 instead of hdc1 and see what happen

---

### Post by virgule on 2006-03-08
ooh now that I think about it..

We could use the live CD to run fsck since we are SURE the drive is not mounted at all!

I don't know what ough to be the realcommand but itshould looklike 'fsck /dev/hdd' right?

---

### Post by Ingla on 2006-03-08
Don't I have to do that in Live CD? Please tell me exactly what to type.

Also, fstab doesn't have it. Doesn't it need an entry like:
/dev/hd1 / ext3 defaults 1 1  ?

Please see if you can help me do this, as I really haven't a clue in the business.

Thanks.

---

### Post by Ingla on 2006-03-08
Your last post came on while I was writing. Don't know what to do first and also don't know whether to run fsck on hdd1 or what...in the end it's supposed to be hdc1.

What do you think? I'm lost.

---

### Post by virgule on 2006-03-08
You know the drive to scan/repair must not be mounted so doing it from the Live-CD is the perfect place. 

The command is:
```

e2fsck -cf /dev/hdd

```


Report the outcome.

---

### Post by Ingla on 2006-03-08
1. How can I be sure it's not mounted? I think it mounts everything in read only, but I saw that that's also dangerous.

2. hdd refers to an IDE device that apparently does not exist. I have hda (primary hd, currently absent), hdb (cd rom), and hdc (secondary hard drive), and fd0 (floppy). There are no other media connected to the machine.

Even if I run fsck on hdd, how can I turn it back to hdc?...Otherwise, presumably it could never boot. If I'm reading the output I sent you correctly, BIOS is listing hdd as a slave of hdc on IDE1. This is some kind of corruption or something...physically, there's no slave drive there (calling the cd rom a slave of hda on IDE0 is normal and physically accurate...I think).

This leaves me in kind of a dilemma. First I have to be sure the drive isn't mounted at all (not even R/O) and second, even if I fsck it as hdd...there's no such thing. So what will be the result in terms of ability to boot back in? 

What do you think?

---

### Post by Ingla on 2006-03-08
By the way, isn't e2fsck the command to run fsck on reboot? If so, it probably can't actually access a nonexistent drive. Maybe I'm wrong?

---

### Post by virgule on 2006-03-08
1- mtab file show what is currently mounted. Use cat and examine the results.
```

cat /etc/mtab

```

2- I refer you to dcstar's post (post #2 of this thread). hdd actually exist. 'dmesg | grep hd' confirmed this.

Actually that is weird. I am puzzled, too... Do you have jumpers on those drives? Perhaps 'jumping' them would force the kernel to assign them the letter you want instead of according to their detection order? I have no clue about that so take this for what its worth.. ;)

Anyway, running e2fsck will, at least, make up our mind about filesystem corruption/errors that might cause this situation.

So, in short, make sure its not mounted with 'cat /etc/mtab' then run 'e2fsck -cf /dev/hdd'. I think I am I just as confused as you :D

---

### Post by Ingla on 2006-03-08
One more problem. It's very late in my time zone and I'm afraid to try any tricky repairs when I'm this tired.

I'm going to try to finish fixing this tomorrow. Thank you very much for you help and I hope to meet you here then.

---

### Post by virgule on 2006-03-08
A good move would be to reconfigure your computer exactly has it was when you installed Linux. I mean to plug all the drives in the exact places (slots?) too.

---

### Post by virgule on 2006-03-08
I see.. Its 19h here. I can log-in anytime after 15h tomorrow. I should be there.

---

### Post by Ingla on 2006-03-08
Got your post just before going out.

Here's the result of cat /etc/mtab:
----------------------------------------------------------------------------------------------------
ubuntu@mygateway:~$ cat /etc/mtab
/dev/mapper/casper-snapshot / auto rw,noatime 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
ubuntu@mygateway:~$
------------------------------------------------------------------------------------------------------

I'm not sure I can read this. Do you see anything that's mounted? 
What is 
/dev /.dev unknown rw,bind 0 0 
?

---

### Post by Ingla on 2006-03-08
Clarification:

When I say hdd doesn't exist, I mean this:

My BIOS usually says:

Primary Master: Hitachi Whatever
Primary Slave: CD ROM
Secondary Master: WDC or Samsung or whatever hard drive
Secondary Slave: None

Somehow, in Linux, it's saying hdd is the secondary slave but, physically, there's no such drive or device. That's what's weird and I have no idea what the ramifications of this are  (I'm pretty sure there can't be any way to boot into it?!?!?!).

Maybe the way to go about this is to try to edit fstab and the boot files? Maybe the kernel is messed up, in which case, I'm in a bit of trouble, never having touched a kernel.

Anyway, we have a night to sleep on it. Maybe someone will see this and join in.

Thanks again for everything.

Good night.

---

### Post by Ingla on 2006-03-09
[SIZE="3"]Hi.

I made tests on the old Ubuntu disk for comparison. As far as I know the results indicate pretty well what should show up on the disk we're trying to fix. There's a lot of output, so I'll try to organize it in some kind of readable fashion.

As mentioned yesterday, I ran tests on both Knoppix and Live CD. The results were not always identical. I ran all the checks on the old disk on the disk itself, with no Live CD.[/SIZE]

---------------------------------------------------------------------------
[SIZE="1"]_**fdisk -l**_
On Knoppix, Live CD and the OLD DISK there was no output.
---------------------------------------------------------------------------
_**cat /etc/fstab**_
- - - - - - - - - - - - - - - - - - -
_Knoppix_
/proc /proc proc defaults 00
/sys /sys sysfs noauto 00
/dev/pts /dev/pts devpts node=0626 00
/dev /fd0 /mnt/auto/floppy auto(?) user,noauto, exec,ro 00
#Added by Knoppix
/dev/hdd1 /mnt/hdd1 ext3 noauto,users,exec 00
#Added by Knoppix
/dev/hdd5 none swap defaults 00
- - - - - - - - - - - - - - - - - - - 
_Live CD_
/dev/mapper/casper-snapshot / auto no??? 00
tempfs /temp tempfs nosuid,nodev 00
/dev/hdd5 swap swap defaults 00
- - - - - - - - - - - - - - - - - - - 
_OLD DISK_
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
- - - - - - - - - - - - - - - - - - - - 
**_cat /boot/grub/menu.lst_**
_On Knoppix and  Live CD_
No such file or directory
- - - - - - - - - - - - - - - - - - - -
_OLD DISK_
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 ) *<spaces added to avoid smilies>*
#            grub-install( 8 ), grub-floppy( 8 ), *<ditto>*
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.
 
## default num
# Set the default entry to the entry number NUM. Numbering starts from
0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default
entry
# is the entry saved with the command 'savedefault'.
default         0
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the
default entry
# (normally the first entry defined).
timeout         3
 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
 
# Pretty colours
#color cyan/blue white/blue
 
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive
editing
# control (menu entry editor and command-line)  and entries protected by 

the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
 
#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#
 
#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
 
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
 
## DO NOT UNCOMMENT THEM, Just edit them to your needs
 
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdc1 ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
 
## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true
 
## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false
 
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single
 
## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash
 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
 
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true
 
## ## End Default Options ##
 
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
 
title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot
 
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
 
title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot
 
title           Ubuntu, kernel 2.6.12-8-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-8-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-8-386
savedefault
boot
 
title           Ubuntu, kernel 2.6.12-8-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-8-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.12-8-386
boot
 
title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot
 
### END DEBIAN AUTOMAGIC KERNELS LIST
- - - - - - - - - - - - - - - - - - - -
**_cat /etc/mtab_** *<DIDN'T RUN THIS ON THE OLD DISK>*
_LIVE CD_
/dev/mapper/casper-snapshot / auto rw,noatime 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
- - - - - - - - - - - - - - - - - - - - -
_**dmesg | grep hd**_ 
_LIVE CD_
ide0: BM-DMA at 0xd400-0xd407, BIOS settings: hda : pio, hdb : DMA <spaces inserted between ":" and adjacent letters to avoid smilies>
ide1: BM-DMA at 0xd408-0xd40f, BIOS settings: hdc : pio, hdd : DMA <ditto>
hdb: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
hdd: SAMSUNG SP0411N, ATA DISK drive
hdd: max request size: 1024KiB
hdd: 78242976 sectors (40060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(33)
hdd: cache flushes supported
hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
Adding 1413680k swap on /dev/hdd5. Priority:-1 extents:1
cdrom: hdb: mrw address space DMA selected
ubuntu@mygateway:~$
- - - - - - - - - - - - - - - - - - - - - - - - - - - -
***<NOTE: The Samsung hard drive seen on hdd is the drive that should be booting as hdc1.>***
- - - - - - - - - - - - - - - - - - - - - - - - - - - -  
_OLD DISK_
[4294667.296000] Kernel command line: root=/dev/hdc1 ro quiet splash
[4294670.269000]     ide0: BM-DMA at 0xd400-0xd407, BIOS settings:
hda : pio, hdb : DMA  *<spaces added to avoid smilies>*
[4294670.269000]     ide1: BM-DMA at 0xd408-0xd40f, BIOS settings:
hdc : DMA, hdd : pio [I]<spaces added to avoid smilies>
[[/I]4294671.316000] hdb: HL-DT-ST GCE-8526B, ATAPI CD/DVD-ROM drive
[4294671.751000] hdc: QUANTUM FIREBALLlct08 08, ATA DISK drive
[4294674.421000] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294674.427000] hdc: max request size: 128KiB
[4294674.441000] hdc: 16514064 sectors (8455 MB) w/418KiB Cache,
CHS=16383/16/63, UDMA(33)
[4294674.441000] hdc: cache flushes not supported
[4294685.760000] Adding 369452k swap on /dev/hdc5.  Priority:-1 extents:1
[4294686.048000] EXT3 FS on hdc1, internal journal
- - - - - - - - - - - - - - - - - - - - - 

[/SIZE]
[SIZE="3"]Those are the data. As mentioned, The old disk was installed the same way as the broken one, i.e., the configuration of IDE devices, etc., was the same. Therefore, I think it probably gives a pretty accurate idea of what outputs should be on the drive that isn't working.

Obviously, something has become pretty well messed up. The question is whether it can be fixed and, if so, how...in the most cautious manner possible.

For example, I don't know what fsck might do (the partition must be unmounted). But, I don't know whether that can get the system to recognize it as hdc1 instead of hdd, which, as mentioned, does not correspond to any existing physical device.

Should it be run? Would it be better to try manually to edit fstab and/or /boot/grub/menu.lst? 

By the way, I can see hdd from the Live CD, but cannot open it. It belongs to root...but what root? Mine or Live CD's? What password? I could at least copy out my how-to's and things if I could gain access (assuming the installation can't be repaired). 

But first, it would be better to try a fix, if anyone thinks it can be done and can suggest anything.

Thanks very much.[/SIZE]

---

### Post by qferret on 2006-03-09
1. <NOTE: The Samsung hard drive seen on hdd is the drive that should be booting as hdc1.> The drive is not mounted anywhere that I have seen in your output postings...fsck should be OK...

2. In order to get the "grep's" "cat's" etc to work, you would need to mount the file system....the method you have been using has been checking the "filesystem" of the live cd's. 

2a. With Ubuntu Live CD:  sudo mkdir /mnt/drive
2b.sudo mount -t auto /dev/hdd /mnt/drive
2c. try the commands used before with a prefix of /mnt/drive (e.g. cat /mnt/drive/etc/fstab and cat /mnt/drive/boot/grub/menu.lst)

If mounting /dev/hdd works...you're probably better off changing the references from hdc1 to hdd....

---

### Post by qferret on 2006-03-09
oh ...btw...Using the ubuntu Live CD, sudo has a password of "ubuntu"

---

### Post by Ingla on 2006-03-10
Thanks.

I'm getting a bit confused as to the order of priorities. 

Should I run those tests again as described...or should I just run fsck (since the partition isn't mounted)...and see if it works? Maybe it can't help me boot in because the directory name has been changed? Can fsck help something like that??

Maybe it's better to have more info first? Or maybe fsck will change some of that info anyway?

Also, how accurate is the info? I mean, if the CD system sees the drive as hdd, does that mean it appears that way "to itself" (without the CD).  Windows, for example, sometimes assigns different names to drives when looking from somewhere else...if I have two drives, each with a C and F partition (when used alone), the second will appear as D and, maybe, G when looking from the other drive.

The boot commands seem to be looking,  unsuccessfully, for hdc1.

What would happen if I could gain access to the subdirectory hdd and copy or rename it to hdc1...and then try to boot directly into the disk? Could that be done from the CD without mounting anything? I can see it in the file system, but it is owned by root (not sure which root).

If I *should* run fsck first, what command should I use from the Live CD, which will fsck the desired partition (from the CD) *without mounting it*?

I'm sure it's obvious that I'm quite confused as to the possibilities and which to try first (while attempting to avoid further damage).

Can anyone bring some order and sense to these rambling thoughts and help me develop a logical plan of action?

Thanks.

---

### Post by virgule on 2006-03-10
So we know the Linux drive is still there (hdd) but it is not where it used to be (hdc). (?!)

My point with 'dmesg | grep hd' from a LiveCD, since you mentionned someone might have pulled it off the hard way,  was to ensure the drive is still functionnal at all. It seam to be but it moved from hdc to hdd for no appearent and logical reasons. Could it be some master/slave jumpers misplacement!?!?  :-k 

It seam obvious to me no amount of fsck anyhow from anywhere could put it back to hdc BUT it could fix some possible unclean unmounting issues, like corruption, if any at all.

So, right now, I would just point GRUB to hdd1 instead of hdc1 and see how it goes? fsck should do its stuffs automatically if need be.

Boot LiveCD. Have a terminal/console:  sudo password should be 'ubuntu'
```

sudo mount -t auto /dev/hdd1 /mnt     #mount the SAMSUNG at /mnt access point
sudo cp /mnt/boot/grub/menu.lst /mnt/boot/grub/menu.lst.backup     #backup GRUB file so we have fallback capability ;)
sudo nano /mnt/boot/grub/menu.lst     #edit GRUB and change hdc1 to hdd1.
<CTRL-x> to save changes

```

What are you thoughts about this?

I am sure it goes down to either jumpers -or- anything else is beyong me. heh

---

### Post by Ingla on 2006-03-10
Thanks.

I don't know what my thoughts are because I just don't know enough about these things.

What would be the next step? Just reboot straight to the hard drive and see what happens?

Your idea doesn't sound dangerous until we get to that stage. Then fsck may kick in, as you say, and it will be working on a mounted root. It may do that at some point anyway...without me asking it to.

(I still can't see how any jumper positions could have changed. All other disks work as usualy...including the old Ubuntu one. No one else on the machine touches Linux. They're Windows guys.) 

So, what do you think? Try what you suggested and boot in?

Thanks.

---

### Post by virgule on 2006-03-11
That is up to you.. I would point the root to hdd1 and just hit it. :)

---

### Post by Ingla on 2006-03-15
Hello.

I was called away for a couple of days. Now I'm back. AND I'm writing from the "broken" Ubuntu disk!

Virgule, you were right all along! Jumpers! I didn't believe it because I **knew** I hadn't changed anything. Also, as mentioned, the other people who use this machine never touch Linux. 

Even so, before trying to mount hdd  and edit grub (which sounded like a long shot) or reformatting, I decided to check the jumpers anyway. You were right. Someone had changed them. Other users still deny having done it. My only explanation is that someone thought he was working with his disk and, by accident, he grabbed mine... and never even realized he had touched it.

There's a lesson! Before worrying about the software and everything else, double check the obvious... is everything connected, etc. It's ABC, but I was so sure that couldn't be the problem I didn't look. Stupid, eh?

Anyway, all's well that ends well. Thanks to everybody for all the help.

---

### Post by virgule on 2006-03-15
"Experience is what you get when you were expecting something else, or just after you need it for the first time."

   --Someone

---

