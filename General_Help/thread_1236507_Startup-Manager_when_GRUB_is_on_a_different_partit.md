---
title: "Startup-Manager when GRUB is on a different partition"
date: 2009-08-10
forum: General Help
---

### Post by angelkiller on 2009-08-10
Hello,

I have Grub installed on a different partition. So there are Grub files in /boot/grub , but those aren't the ones that are used to boot.

So my issue is with using the Startup Manager. It, by default, opens up the Grub files in /boot/grub. But making changes to those files has no effect on my boot process. (for reasons listed above)

So I was wondering if there is a way to make the Startup Manager point to a Grub directory other than the default /boot/grub?

Thanks. :)

---

### Post by LowSky on 2009-08-10
what changes are ou trying to make, you could always edit things by hand.

---

### Post by angelkiller on 2009-08-22
Sorry for the late response.

Anyway, yes I could make the changes by hand. In fact, that's what I've been doing so far. I'd use the Startup-Manager to make the changes to the /boot/grub/ files and then copying the directory over to where I have it actually installed.


I'm not trying to change anything in particular, it just would be easier to make changes with a graphical interface. (for me) Does the Startup-Manager have any config files that point to /boot/grub?

Thanks again.

---

### Post by jheaton5 on 2009-08-22
I don't understand what you are trying to do.

I have a dual boot installation of Debian and Ubuntu.  Grub is installed on the Debian partition.  The /boot/grub/menu.lst file that is used at boot is the one on the Debian partition.  When Ubuntu releases a kernel update, the /boot/grub/menu.lst on the Ubuntu partition is updated, but not the one on the Debian partition.  I have to update the Debian: /boot/grub/menu.lst manually to match the Ubuntu: /boot/grub/menu.lst changes.

Is this what you are trying to do?  If not, please be more specific.

---

### Post by angelkiller on 2009-08-22
I dual boot XP and Ubuntu and have GRUB installed on a separate partition. So when my system boots the files on the separate partition for GRUB are used. So editing the files in /boot/grub have no effect on booting.

I would like to use the Startup Manager to edit the GRUB files on my seperate partition because I find it easier to use than editing the files manually.

But by default, the Startup manager edits the files in /boot/grub, which isn't helpful to me.

Hopefully that was clearer... If something still doesn't make sense, let me know. 


And I now have a second question, does the Startup Manager only edit the /boot/grub/menu.lst file? Or do some of the settings change other files as well.

Thanks.

---

### Post by michy99 on 2009-08-22
Have you tried making /boot/grub/menu.lst a link to the actual menu.lst?

---

### Post by angelkiller on 2009-08-22
> **michy99 said:**
> Have you tried making /boot/grub/menu.lst a link to the actual menu.lst?
At one point I did try that, but for some reason that solution wouldn't work. Unfortunately, I can't remember why...

Do you know of a quick command that'll point /boot/grub/menu.lst to /media/GRUB/boot/grub/menu.lst?

---

### Post by jheaton5 on 2009-08-22
I understand your issue.

I have never used startupmanager.  I just installed it to see if I could answer your question.  I do not find a place to change devices or partitions.  It appears to use only the partition on which it is installed.

Can you mount the partition where Grub is installed and find a /boot/grub/menu.lst file in that partition?

I see from the above post that you do have a /boot/grub/menu.lst in the Grub partition.  Can you not just mount that partition and edit that file using sudo nano or gksudo gedit?

---

### Post by angelkiller on 2009-08-22
> **jheaton5 said:**
> Can you mount the partition where Grub is installed and find a /boot/grub/menu.lst file in that partition?
Maybe I don't fully understand your question...

Yes I can mount that partition and yes there is a menu.lst file there.

The partition that Grub is installed is mounted in media/GRUB/ and the menu.lst file is /media/GRUB/boot/grub/menu.lst.

Hopefully that answers your question.

And yes, I can edit /media/GRUB/boot/grub/menu.lst with nano or geidt. However, I found it easier to use a graphical interface.

For example, I'm not sure how to manually define themes or set the screen resolution or color depth. But the Startup Manager has simple settings where I can change those options.

---

### Post by michy99 on 2009-08-22
I started the Startup Manager from a terminal and noticed that it searches for menu.lst. Maybe if you get rid of the first menu.lst (or rename it) the Startup Manager will continue to search until it finds the other one.

---

### Post by angelkiller on 2009-08-22
> **michy99 said:**
> I started the Startup Manager from a terminal and noticed that it searches for menu.lst. Maybe if you get rid of the first menu.lst (or rename it) the Startup Manager will continue to search until it finds the other one.
That's very interesting. Let me play around with that and see if I can get anywhere.

**Edit 1:**
I renamed the /boot/grub directory to something else. Here's the terminal output of running the Startup manager:
```
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###
```
When the actual program window showed up, no options were availible. It was pretty much a blank window. It would seem that the Startup Manager is hard coded to look in/for /boot/grub and nowhere else...?

---

### Post by jheaton5 on 2009-08-22
> **michy99 said:**
> I started the Startup Manager from a terminal and noticed that it searches for menu.lst. Maybe if you get rid of the first menu.lst (or rename it) the Startup Manager will continue to search until it finds the other one.

Don't get rid of it, jut rename it.  You'll need the data on that file later.

---

### Post by michy99 on 2009-08-22
Okay, let's go at this from a different direction. If I understand correctly, you have a separate /boot partition which is what Grub actually uses to boot, and you also have a /boot directory on your main partition which is where Startup Manager looks to find menu.lst.

It seems the answer would be to get rid of the contents of /boot on the main partition, and mount the /boot partition at /boot when you boot up by adding a line to fstab.

---

### Post by angelkiller on 2009-08-22
Ok, I think I got it.

I renamed /boot/grub to /boot/grub-original. Then I made a (symbolic) link so that /boot/grub points to /media/GRUB/boot/grub. I started the Startup Manager and surprisingly the settings that I had specified in my GRUB partition were loaded.

So everything *seems* to be working *so far*. Let me change some settings and restart my system so I confirm everything is working as it should. 

**Edit:**
This solution is confirmed as _working_.

I suppose my previous attempt at creating a link failed because the I only made a link to the menu.lst file. Linking the whole directory seemed to have done the trick.

---

### Post by jheaton5 on 2009-08-22
Great.  How did you make a symbolic link?  That's a trick I haven't learned yet.

---

### Post by angelkiller on 2009-08-22
> **jheaton5 said:**
> Great.  How did you make a symbolic link?  That's a trick I haven't learned yet.
I had to look it up too. :P [But the command is simple](http://ubuntuforums.org/showpost.php?p=1488224&postcount=2).



> **michy99 said:**
> Okay, let's go at this from a different direction. If I understand correctly, you have a separate /boot partition which is what Grub actually uses to boot, and you also have a /boot directory on your main partition which is where Startup Manager looks to find menu.lst.

It seems the answer would be to get rid of the contents of /boot on the main partition, and mount the /boot partition at /boot when you boot up by adding a line to fstab.
I think I've just done what you've said in a more roundabout way.

I should have my partition that has GRUB on it mounted in /boot/grub. And I suppose I could use fstab to automate the mounting process.

---

### Post by michy99 on 2009-08-22
Yeah, either way should work.

---

### Post by angelkiller on 2009-08-22
Ok, now I'd like to streamline this setup.

Right now grub is installed on a seprate partition, but in that partition it's in the directory /boot/grub.

If I were to mount that partition in by current /boot/grub directory, you'd get a mess of repetitiveness. (the menu.lst file would be located in /boot/grub/boot/grub/menu.lst)

In the end, I'd like to have the Grub files in the root directory of that partition and to have that partition automatically mounted in /boot/grub upon startup.

My attempt at making that work didn't work. Can anyone give me a simple walkthrough? Thanks.

---

### Post by mike555 on 2009-08-22
You might try " GAG " bootloader .

---

### Post by michy99 on 2009-08-22
What other files are on the partition with the grub files?

---

### Post by angelkiller on 2009-08-22
> **michy99 said:**
> What other files are on the partition with the grub files?
Nothing else.

---

### Post by michy99 on 2009-08-22
So the partition has one directory, /boot, and that directory has one directory, /grub, which has your grub files?

---

### Post by angelkiller on 2009-08-22
> **michy99 said:**
> So the partition has one directory, /boot, and that directory has one directory, /grub, which has your grub files?
Yes.

---

### Post by michy99 on 2009-08-22
Assuming that the partition is mounted at /media/GRUB:```
sudo cp /media/GRUB/boot/grub/* /media/GRUB
```Then, after you are sure that everything has been copied to /media/GRUB, remove the originals.```
sudo rm -r /media/GRUB/boot
```To automatically mount it at boot, edit fstab.```
gksudo gedit /etc/fstab
```Add this line:```
/dev/sdXX /boot/grub    ext3    relatime    0   2

```Replace sdXX with whatever partition you are mounting.

Save and check to see if it works.```
sudo mount -a
```

---

### Post by michy99 on 2009-08-22
I forgot to mention that you have to get rid of the link that you created and make a mount-point at /boot/grub.```
sudo rm /boot/grub
sudo mkdir /boot/grub
```

---

### Post by louieb on 2009-08-22
> **angelkiller said:**
> In the end, I'd like to have the Grub files in the root directory of that partition and to have that partition automatically mounted in /boot/grub upon startup.

Just a guess you have whats called a **dedicated grub partition**? 
If so you need to look at two grub commands **configfile and chainloader**
[IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")  more about configfile and chainloader can be found on the same page.

---

### Post by angelkiller on 2009-08-22
> **michy99 said:**
> Assuming that the partition is mounted at /media/GRUB:```
sudo cp /media/GRUB/boot/grub/* /media/GRUB
```Then, after you are sure that everything has been copied to /media/GRUB, remove the originals.```
sudo rm -r /media/GRUB/boot
```To automatically mount it at boot, edit fstab.```
gksudo gedit /etc/fstab
```Add this line:```
/dev/sdXX /boot/grub    ext3    relatime    0   2

```Replace sdXX with whatever partition you are mounting.

Save and check to see if it works.```
sudo mount -a
```
Works! :KS

But since I've moved my Grub files around, do I have to reinstall Grub? I'm afraid to reboot my computer right now.

> **louieb said:**
> Just a guess you have whats called a **dedicated grub partition**? 
If so you need to look at two grub commands **configfile and chainloader**
[IDBS make a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")  more about configfile and chainloader can be found on the same page.
IIRC, that's the same page I used when I made the separate Grub partition. I'm reading now.

---

### Post by louieb on 2009-08-23
> **angelkiller said:**
> Works! :KS...But since I've moved my Grub files around, do I have to reinstall Grub? I'm afraid to reboot my computer right now....IIRC, that's the same page I used when I made the separate Grub partition. I'm reading now.

Yes if you moved the grub file **stage2** you will need to setup the MBR to find stage2 in its new location. 

:)- from your last post - looks like you have created a hybrid of a dedicated GRUB partition and a separate /boot partition. Something to say to your geeky friends - hey look at this.

---

### Post by angelkiller on 2009-08-23
> **louieb said:**
> Yes if you moved the grub file **stage2** you will need to setup the MBR to find stage2 in its new location. 

:)- from your last post - looks like you have created a hybrid of a dedicated GRUB partition and a separate /boot partition. Something to say to your geeky friends - hey look at this.
Ooops. So my laptop hibernated... :(

Now Grub won't boot, but I understand why. Any way to get back into my machine?

---

### Post by louieb on 2009-08-23
No grub menu or get grub menu but entries don't work? 

No grub menu -  the catlett method should work for you. [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

he has one instruction you need to change if the 1st find command does not get a hit try the one listed here. 
```
find  /boot/grub/stage2
find  /grub/stage2
find /stage2
```

the rest of the how to will sill apply to you.

---

### Post by angelkiller on 2009-08-23
> **louieb said:**
> No grub menu or get grub menu but entries don't work? 

No grub menu -  the catlett method should work for you. [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

he has one instruction you need to change if the 1st find command does not get a hit try the one listed here. 
```
find  /boot/grub/stage2
find  /grub/stage2
find /stage2
```

the rest of the how to will sill apply to you.

Ok, only the third command returned something. (which was '(hd0,1)')

But when I went to run 'setup (hd0)' I got an error about somthing being missing. Unfortunately, in my haste, I didn't take note of exactly what.

At that point, I saw that my seperate partition with the Grub files on it was accessable via the live CD. So I simply re-created my boot/grub directory on that partition and copied the files back there. So I had what I had before I changed anything. Reboot, and everything works.


So now, I'm back where I was at post #27. I need to configure Grub so the stage 2 file(s) will be correctly located. Before they were in my seperate partition, in a directory /boot/grub/. Now they have been *copied* (not moved) to the root directory of that partition.

I'm a bit confused about how my setup works with regards to mounting the partition. You see, my partition with grub on it has always automatically mounted (or detected, I'm not sure. It always shows up in the Places menu) in /media/GRUB. But how does Grub boot if that partition isn't mounted?

Maybe I'm asking the wrong questions. (I'm very confused here) To what extent does Grub follow the local file system? For example if the Stage 1 files automatically look in /boot/grub for the stage 2 files, what happens if /boot/grub doesn't exist? In my case, I would want that grub partition to be mounted in /boot/grub. But how will Stage 1 find /boot/grub if it has yet to be mounted by the OS?

I don't think any of my questions make sense. So if you just tell me something, I'll tell you what I get or don't get and we can work from there. :)

---

### Post by louieb on 2009-08-24
At the point when GRUB loads nothing is mounted anywhere. It gets hard drive information from BIOS  and  can read the partition table and thats about it.  When you setup GRUB your building custom MBR code to load the stage2 file.  

Other than playing around just wondering if there is something your trying to accomplish by moving the Grub files from their default setup?

One very nice tool is the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")  it can be run from a live CD or your hard drive install. just** cd to the directory you downloaded it to**.

```
sudo bash boot_info_script*.sh
```It creates a file named RESULTS.TXT    and it would be good to include it in your next post. 

> But when I went to run 'setup (hd0)' I got an errordid you run 'root (hd0,1)' or whatever you got from the find command 1st. Need to do that.

[Boot Info Script - run from live CD Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3")

---

### Post by angelkiller on 2009-08-24
I get what you're saying about Grub. I need the Stage 1 file to point to that partition with Grub on it. (rather than my through my Ubuntu partition via /boot/grub)

And I suppose I haven't explained why I set everything up this way. Usually, I use Ubuntu as my main OS and XP as a fallback. I like playing around with multiple OSs, so I may have a third or even fourth OS installed. Well once, I did this and the third OS installed its own version of Grub. Everything worked fine until I wanted to get rid of that OS. So when I wiped the partition, I wiped out Grub, locking myself out of my system. I needed a way to boot my system that was OS independent. So I made a partition with Grub on it so it didn't matter what happened to any OS, I could still boot my system. At the time, it made the most sense.

Here's my RESULTS.txt file:
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 194563215.
    Boot file info:     Grub0.97 in the file /stage1 looks at sector 1 of the 
                       same hard drive for the stage2 file. A stage2 file is 
                       at this location on /dev/sda. Stage2 looks on the same 
                       partition for /boot/grub/stage2.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc5fbc5f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    30,716,279    30,716,217   7 HPFS/NTFS
/dev/sda2         194,563,215   195,366,464       803,250   b W95 FAT32
/dev/sda3         192,506,895   194,563,214     2,056,320  82 Linux swap / Solaris
/dev/sda4          30,716,280   192,506,894   161,790,615   5 Extended
/dev/sda5          30,716,343    61,432,559    30,716,217  83 Linux
/dev/sda6          61,432,623    81,915,434    20,482,812  83 Linux
/dev/sda7          81,915,498   102,398,309    20,482,812  83 Linux
/dev/sda8         102,398,373   192,506,894    90,108,522  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4684464884463B27" LABEL="Windows" TYPE="ntfs" 
/dev/sda2: LABEL="GRUB" UUID="D207-53D6" TYPE="vfat" 
/dev/sda3: UUID="fb772674-424b-431e-8566-bcb82b11e618" TYPE="swap" 
/dev/sda5: UUID="4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f" TYPE="ext4" 
/dev/sda8: LABEL="Data" UUID="606a34e1-5b2f-4630-b289-bc036404c819" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda8 on /home type ext3 (rw,relatime)
/dev/sda2 on /boot/grub type vfat (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/maxx/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=maxx)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black white/green

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		" "
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


================================ sda2/menu.lst: ================================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black white/green

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		" "
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=================== sda2: Location of files loaded by Grub: ===================


  99.6GB: boot/grub/menu.lst
  99.6GB: boot/grub/stage2
  99.6GB: menu.lst
  99.6GB: stage2

=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color green/black white/green

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		" "
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4bb23cc4-64a3-4ed0-89dd-c871fcf4d46f /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=606a34e1-5b2f-4630-b289-bc036404c819 /home           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=fb772674-424b-431e-8566-bcb82b11e618 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


# Added by Max F to make my Grub partition mount in /boot/grub automatically on boot
/dev/sda2 /boot/grub    vfat    relatime    0   2

=================== sda5: Location of files loaded by Grub: ===================


  15.7GB: boot/grub/menu.lst
  15.7GB: boot/grub/stage2
  16.9GB: boot/initrd.img-2.6.28-11-generic
  18.9GB: boot/initrd.img-2.6.28-13-generic
  19.2GB: boot/initrd.img-2.6.28-14-generic
  19.7GB: boot/initrd.img-2.6.28-15-generic
  17.6GB: boot/vmlinuz-2.6.28-11-generic
  18.8GB: boot/vmlinuz-2.6.28-13-generic
  19.2GB: boot/vmlinuz-2.6.28-14-generic
  18.8GB: boot/vmlinuz-2.6.28-15-generic
  19.7GB: initrd.img
  19.2GB: initrd.img.old
  18.8GB: vmlinuz
  19.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  7d 16 91 d7 05 47 19 0f  48 6c 11 ae 16 d0 f0 68  |}....G..Hl.....h|
00000010  5f e9 0e 9c 32 3c 9b a8  49 16 64 c1 87 0b 1d 12  |_...2<..I.d.....|
00000020  8f 50 b3 41 d5 e0 b8 cb  4a 3a b2 36 5d 79 17 1c  |.P.A....J:.6]y..|
00000030  df f9 5f 47 01 e8 f0 7f  14 59 f2 10 d3 6d be 87  |.._G.....Y...m..|
00000040  5a ea a0 01 e2 7f 3c b1  85 b5 6a 2c 62 03 e2 0d  |Z.....<...j,b...|
00000050  05 52 33 b2 2d 27 db f4  59 31 71 00 6f ad 79 66  |.R3.-'..Y1q.o.yf|
00000060  78 a2 3b 80 6d 58 f6 a2  d3 5f 2a 5a 64 d0 16 9d  |x.;.mX..._*Zd...|
00000070  b7 a9 8b dc 05 d9 5d 04  89 43 28 f4 42 fd b0 56  |......]..C(.B..V|
00000080  39 21 d2 fc 5a 7c 62 42  71 26 83 47 f8 6c 4d 7d  |9!..Z|bBq&.G.lM}|
00000090  18 c2 64 b0 8d 82 9b c1  0d 16 a1 5a f1 c0 2e 06  |..d........Z....|
000000a0  5f 4e ed 8f b4 30 ca 87  4a 9b 7f b8 dd 36 4c 8b  |_N...0..J....6L.|
000000b0  bc 01 39 3c e7 4c c8 a4  da ee 0f c2 94 64 70 e0  |..9<.L.......dp.|
000000c0  b5 a6 9e d7 87 6b 4f de  2c b8 7e 60 4d 8d 9e 51  |.....kO.,.~`M..Q|
000000d0  03 e9 c4 6d 3a 51 f7 72  b5 4b ed 85 a2 28 82 bf  |...m:Q.r.K...(..|
000000e0  22 5c e4 09 7f 4e 45 7c  8e 33 67 4f 63 24 e7 b8  |"\...NE|.3gOc$..|
000000f0  b3 48 23 47 41 57 0c 2a  13 3d 9b f4 38 3a e5 80  |.H#GAW.*.=..8:..|
00000100  78 17 8b 2d b7 1c 4e df  4f b5 8d 9c f3 12 cc aa  |x..-..N.O.......|
00000110  bc a0 ba 06 65 b1 e1 71  bc 9c c5 18 c9 d5 48 18  |....e..q......H.|
00000120  fc 63 32 1d 8e 17 2f e6  32 34 e7 9d 4f 92 77 5b  |.c2.../.24..O.w[|
00000130  74 1d 46 e3 f4 e9 46 c3  08 63 55 dd 4a 7c eb 87  |t.F...F..cU.J|..|
00000140  4a 8f 62 23 92 a7 d1 36  5e e7 91 83 e3 10 0f 55  |J.b#...6^......U|
00000150  51 ef 90 06 ac a4 26 8c  a4 d2 0c 70 cb 02 99 12  |Q.....&....p....|
00000160  fb ee 36 36 11 35 5a 58  98 8a 58 97 cd 62 5e 69  |..66.5ZX..X..b^i|
00000170  cd 2b 91 13 18 ca 39 8c  68 73 2f 1b 90 48 76 30  |.+....9.hs/..Hv0|
00000180  76 0f ae 90 90 59 bd 11  a8 4a 25 d1 ad 12 ac b7  |v....Y...J%.....|
00000190  13 62 a0 fc 47 2d 7b 8e  ce 04 04 c1 9b 64 91 67  |.b..G-{......d.g|
000001a0  26 d0 b3 cb 96 be b0 36  10 06 de a3 8b 1d 43 0e  |&......6......C.|
000001b0  a2 9f 12 3c 0b 21 43 d9  c9 dd 3f 24 4b e7 2d 00  |...<.!C...?$K.-.|
000001c0  76 e3 b0 43 60 52 37 4f  22 fe c8 ec 62 30 88 f7  |v..C`R7O"...b0..|
000001d0  de 9b 32 45 5e 5e 0b 59  97 68 c0 71 1d 53 d3 b6  |..2E^^.Y.h.q.S..|
000001e0  86 de 55 49 e8 03 a5 a5  73 e8 bd 29 00 c6 0f 8d  |..UI....s..)....|
000001f0  92 a9 f0 f3 b7 94 78 6b  11 7a f2 de 02 15 fe d0  |......xk.z......|
00000200

Unknown BootLoader  on sda7

00000000  02 32 64 61 63 32 31 65  65 2d 37 35 66 62 2d 34  |.2dac21ee-75fb-4|
00000010  39 65 35 2d 62 61 33 39  2d 37 36 31 30 32 38 65  |9e5-ba39-761028e|
00000020  30 33 32 31 61 02 40 29  03 55 02 32 65 35 35 31  |0321a.@).U.2e551|
00000030  34 63 61 2d 62 39 62 35  2d 34 30 38 38 2d 61 39  |4ca-b9b5-4088-a9|
00000040  38 36 2d 65 37 30 66 61  38 35 61 32 36 38 35 02  |86-e70fa85a2685.|
00000050  ea 28 03 55 01 32 65 38  61 35 65 30 35 2d 66 34  |.(.U.2e8a5e05-f4|
00000060  32 63 2d 34 65 36 64 2d  39 32 34 37 2d 38 32 33  |2c-4e6d-9247-823|
00000070  39 39 33 63 39 64 62 39  36 09 29 03 55 02 32 65  |993c9db96.).U.2e|
00000080  64 63 39 65 39 37 2d 37  39 61 32 2d 34 37 66 30  |dc9e97-79a2-47f0|
00000090  2d 62 63 31 61 2d 36 62  63 66 64 30 35 37 32 38  |-bc1a-6bcfd05728|
000000a0  61 39 02 35 29 03 55 02  32 66 33 62 37 61 33 61  |a9.5).U.2f3b7a3a|
000000b0  2d 33 30 34 36 2d 34 35  39 35 2d 61 36 32 39 2d  |-3046-4595-a629-|
000000c0  36 35 62 33 31 66 34 34  39 35 61 35 02 ab 28 03  |65b31f4495a5..(.|
000000d0  55 01 32 66 64 37 38 36  38 31 2d 38 33 63 63 2d  |U.2fd78681-83cc-|
000000e0  34 64 32 33 2d 62 34 33  61 2d 63 65 61 30 38 30  |4d23-b43a-cea080|
000000f0  65 37 39 33 61 34 3d 28  03 55 01 32 66 65 63 30  |e793a4=(.U.2fec0|
00000100  35 31 38 2d 33 32 39 63  2d 34 66 39 62 2d 38 64  |518-329c-4f9b-8d|
00000110  66 34 2d 30 35 36 62 31  39 64 39 37 34 35 39 07  |f4-056b19d97459.|
00000120  29 03 55 02 33 30 33 33  65 38 62 30 2d 32 38 39  |).U.3033e8b0-289|
00000130  31 2d 34 65 30 32 2d 61  36 35 33 2d 34 37 36 66  |1-4e02-a653-476f|
00000140  63 63 64 62 31 64 35 38  02 7c 29 03 55 02 33 30  |ccdb1d58.|).U.30|
00000150  36 39 63 64 64 66 2d 31  63 63 66 2d 34 38 61 39  |69cddf-1ccf-48a9|
00000160  2d 39 30 66 31 2d 64 63  37 65 61 38 39 38 37 35  |-90f1-dc7ea89875|
00000170  62 37 01 bd 29 03 55 02  33 30 37 62 63 34 35 66  |b7..).U.307bc45f|
00000180  2d 66 64 66 36 2d 34 39  38 36 2d 62 38 31 37 2d  |-fdf6-4986-b817-|
00000190  65 62 35 61 33 39 31 66  35 30 37 30 02 e1 29 03  |eb5a391f5070..).|
000001a0  55 02 33 30 39 30 36 61  35 38 2d 31 64 64 33 2d  |U.30906a58-1dd3-|
000001b0  34 36 33 34 2d 61 30 37  30 2d 39 34 64 63 36 65  |4634-a070-94dc6e|
000001c0  61 33 65 37 33 65 02 d1  29 03 55 02 33 30 61 37  |a3e73e..).U.30a7|
000001d0  62 61 63 36 2d 31 63 38  66 2d 34 34 34 62 2d 62  |bac6-1c8f-444b-b|
000001e0  66 34 62 2d 62 38 65 35  61 35 39 31 64 39 37 66  |f4b-b8e5a591d97f|
000001f0  02 4b 29 03 55 02 33 30  62 38 39 36 32 38 2d 63  |.K).U.30b89628-c|
00000200
```

And yes, I did run 'root (hd0,1)'. But no need to worry about that, I can get into my system now. I could have  mistyped something.

---

### Post by louieb on 2009-08-24
> I needed a way to boot my system that was OS independent. So I made a partition with Grub on it so it didn't matter what happened to any OS, I could still boot my system. At the time, it made the most sense.
ok I call doing that creating a dedicated GRUB partition. 

But now I see you were trying to go a step further and  manage it with Startup-Manager. In doing so you mounted in your Ubuntu install. Just wonder how that is going to work out next time there is a Kernel update. 

At least i learned something new. Did not you could copy the grub files to partition formated fat32. Mount the partition and have it all work.  Thought GRUB had to be on an ext2 or or some other  Open Source formated partition.

---

