---
title: "looking for diagnostic commands to repair master boot record"
date: 2012-01-09
forum: General Help
---

### Post by imachavel on 2012-01-09
When I restart the computer, the hard drive at boot says 'no operating system found.' I put the gparted disk in the cd drive and booted to it. It seems both partitions still exist. Is the boot sector corrupted? If I run grub.conf will it help?

You probably want to see /dev/sda or /dev/sdb

However, if better commands are available, such as linux equivalent to fixmbr, I'm will to try that as well.
Forgot to mention, booting to the live cd is what I was assuming would be able to get me into the terminal so I could give a diagnostic read out. I should also clarify, it's what I've booted to right now.

---

### Post by dino99 on 2012-01-09
'no operating system found.' is a grub message. It means that it cant find the path to boot.

from a livecd, if you want it installed on sda, then in a terminal:

sudo grub-install /dev/sda
sudo update-grub

then try to reboot normally from hdd

---

### Post by imachavel on 2012-01-09
here is what I get:

sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I'm not sure why the hard drive cannot be found, but gparted can see the partitions on the hard drive. Does that make sense at all?

---

### Post by dino99 on 2012-01-09
how is /etc/fstab ?

sudo fdisk -l

---

### Post by bluexrider on 2012-01-09
I think you want to use a Ubuntu Live CD not sure if the Gparted Live CD can do it.

---

### Post by oldfred on 2012-01-09
Often best to check on what is installed where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

And this runs boot script and often makes repairs:

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by imachavel on 2012-01-09
> **dino99 said:**
> how is /etc/fstab ?

sudo fdisk -l

root@ubuntu:/etc# cd /fstab/
bash: cd: /fstab/: No such file or directory
root@ubuntu:/etc# /etc/fstab
bash: /etc/fstab: Permission denied
root@ubuntu:/etc# sudo fstab
sudo: fstab: command not found
root@ubuntu:/etc# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ded99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95379456   658579455   281600000   83  Linux
/dev/sda2       658581502   976771071   159094785    5  Extended
/dev/sda5       853129216   924809215    35840000   82  Linux swap / Solaris
/dev/sda6       658581504   776222719    58820608   83  Linux
/dev/sda7       776224768   781449215     2612224   82  Linux swap / Solaris

Partition table entries are not in disk order


well doesn't look good

---

### Post by imachavel on 2012-01-09
> **bluexrider said:**
> I think you want to use a Ubuntu Live CD not sure if the Gparted Live CD can do it.

well I was hoping I could fix it from gparted without having to delete all the partitions, reformat, then reinstall the entire OS, I would probably dual boot with linux mint and windows xp in that case. But I hate dual booting windows and linux, it seems to cause grub issues, and I'm sure I've used up my windows activation key too many times, and honestly forgot how to crack the WAT, except with windows 7 you can use slic loader, if you remove security updates. Anyway I don't want to bring that up, as it could be bannable. I could always call up microsoft and ask for a new activation key.

Anyway Let's skip that if I have to reformat then I will just virtualize windows and reformat to how I am running it now, with linux mint on one partition and ubuntu on the other. No idea what messed up master boot record though

---

### Post by JKyleOKC on 2012-01-09
> **imachavel said:**
> root@ubuntu:/etc# cd /fstab/
bash: cd: /fstab/: No such file or directory
root@ubuntu:/etc# /etc/fstab
bash: /etc/fstab: Permission denied
root@ubuntu:/etc# sudo fstab
sudo: fstab: command not foundTry this: ```
less /etc/fstab
```Or you can use "cat" instead of "less" if it's less than a full screen of text.

---

### Post by imachavel on 2012-01-09
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sda7 swap swap defaults 0 0


I got that output, does that help at all? Thanks

---

### Post by JKyleOKC on 2012-01-09
It appears that somehow the main filesystem "/" got deleted from /etc/fstab so it's not getting mounted. You need to add this line to that file: ```
/dev/sda1 /      ext2  errors=remount-ro 0 1
```To do so you'll need to use ```
gksudo gedit /etc/fstab
```You may need to have "ext3" or "ext4" in the third column instead of "ext2" but I believe that the ext2 type should work properly with both of the newer versions. However I would avoid writing to the disk as much as possible until someone else verifies that this is the case!

You also may need a similar line for "/dev/sda6" since it shows up in your fdisk output. However I would not add that line initially, since it will need to use a different mount point instead of "/" and until you get things to boot properly there's not a lot of way to determine what it should be.

The Gparted CD may show you the types for sda1 and sda6; if it does, use those instead of "ext2" in both lines.

Do you actually have two different installations on that drive? This is a most unusual situation, and I've not seen anything exactly like it before, in nearly a dozen years of working with Linux.

---

### Post by imachavel on 2012-01-09
two different partitions, crap. Should I boot up gparted and write down the exact partitions then come back to the thread so we can modify those lines?

---

### Post by imachavel on 2012-01-09
ok look this is what is in text editor:

overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sda7 swap swap defaults 0 0

in fstab (/etc) - gedit

I hate to ask for a big favor, but if you were going to rewrite it, then have me reboot the computer. How would you rewrite it?

Most unusual case ever eh? :popcorn: sounds like something I've said every day of my life working on a computer, just about every day I'm like "this is the most unusual **** I've ever seen" lol.

You never really get used to how unusual the case is do you??

---

### Post by oldfred on 2012-01-09
Are you sure you are not looking at the fstab from the liveCD? 

Boot script gives a complete picture of system.

---

### Post by JKyleOKC on 2012-01-09
> **imachavel said:**
> I hate to ask for a big favor, but if you were going to rewrite it, then have me reboot the computer. How would you rewrite it?I'll give it a try, but will need the "type" information that Gparted shows for each of the partitions. The two at sda1 and sda6 are the heart of the problem, apparently, but it's not really possible to tell from the outside what's in each of them. The one at sda1 is much larger than the one at sda6, so my initial guess would be that sda6 is "/" and sda1 is "/home" but if it was the other way round your data could be damaged.

If you have the Live CD, try booting from it, choosing "try without installing," and then opening the partitions on the HD via the "places" icon (they will probably be labelled as "500GB something" but may have other labels) to see what each of them contains. The one with "/boot" and "/bin" in it, among others, will be the one to mount as "/" and the content of the other one will tell us what it is. With that information, and the type of each from Gparted, I should be able to compose an fstab file that will let you boot without damage.

I may be a bit slow getting back to you with it since it's getting near supper time here but don't give up!

EDIT: Go with OldFred's advice, too; the more information we have, the more we can help!

---

### Post by imachavel on 2012-01-09
yes:

ubuntu@ubuntu:~$ cfdisk

ubuntu@ubuntu:~$ fdisk
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ fdisk -l


it is clearly looking in the live cd. Here is what I'm going to do, simplest fastest easiest method. What I am going to do is boot up gparted, write down everything on a piece of paper, then return to this thread. Hey thanks a ton, don't worry how long you take. Take your time it's the best way the one and only way the Steely Danny whatever way. Haha you heard that song?

---

### Post by topsites on 2012-01-09
Assuming you really did pay for it and assuming that part about using the key too many times is true, the easy answer is to stay away from Windows alltogether... I mean true or not it pisses me off, even if you do pay for it the OS is only good for somewhere between 2-8 years, all depending how soon the next generation architecture comes out and how soon they decide a whole new kernel is needed, sooner or later something won't be backwards compatible, at times perhaps intentional but it doesn't really matter... Only a matter of time, the bottom line is every so many years users WILL pay for a new version of Windows.

And now the bit with the key, does it really fail on a legitimate copy, I am unfortunately sure it does but as always it's a double-edged sword, in some cases it will be true and in others merely an excuse, we have no way to ascertain who speaks the truth so I'm not entirely unsympathetic of Microsoft's position either but ultimately if you want a free Operating System legally, Windows is likely not the answer.

That having been said...
[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

---

### Post by imachavel on 2012-01-09
yes I understand and it is a risk in itself to use open source, as most video games don't work(just about anything else does) of course I'm a video game fanatic. Yes I did pay for it, and yes of course you can torrent cracked copies. Still, they should allow you to use your activation key a number of times before 'flagging it' as inactive, it must take a huge data base to keep track of all the copies of activation keys. Also, think about this, the backwards compatibility, it's a bummer with windows all together. Some old stuff there isn't old drivers for newer versions of the OS made, the older versions of windows, no longer are drivers made for older versions of windows for newer hardware/printers/ etc. Anyway.................

---

### Post by imachavel on 2012-01-09
> **JKyleOKC said:**
> I'll give it a try, but will need the "type" information that Gparted shows for each of the partitions. The two at sda1 and sda6 are the heart of the problem, apparently, but it's not really possible to tell from the outside what's in each of them. The one at sda1 is much larger than the one at sda6, so my initial guess would be that sda6 is "/" and sda1 is "/home" but if it was the other way round your data could be damaged.

If you have the Live CD, try booting from it, choosing "try without installing," and then opening the partitions on the HD via the "places" icon (they will probably be labelled as "500GB something" but may have other labels) to see what each of them contains. The one with "/boot" and "/bin" in it, among others, will be the one to mount as "/" and the content of the other one will tell us what it is. With that information, and the type of each from Gparted, I should be able to compose an fstab file that will let you boot without damage.

I may be a bit slow getting back to you with it since it's getting near supper time here but don't give up!

EDIT: Go with OldFred's advice, too; the more information we have, the more we can help!

ok does THIS help you in any way, shape, or form??



/dev/sda - Gparted

unallocated unallocated 45.48 Gib
/dev/sda1    ext3             268.55 Gib
/dev/sda2    extended      151.72 Gib
/dev/sda6    ext4              56.10
/dev/sda7     linux-swap    2.49 Gib
unallocated    unallocated     34.18 Gib
/dev/sda5      linux-swap      34.18 Gib
unallocated    unallocated      24.78 Gib
unallocated     unallocated      1.02 Mib


I'm just hoping that helps a little bit

---

### Post by JKyleOKC on 2012-01-09
Yes, it does help. It shows that sda1's type is "ext3" and sda6 is "ext4." However we still need to know for sure which of those two is the actual main partition; it could be either. Booting from the Live CD, then using the "places" window to view both partitions is the next step. The main partition will include a number of directories but only a very few files; among the directories will be "/root" and "/bin" which should help identify it. The other partition might be "/home" but it could be most anything else. If you see a directory with your user name, then it's probably "/home" but it could be most anything.

Once we know which is which, I can put together an fstab file for you to copy in and we can see if that makes things bootable. Even if we can only identify which is the main one, we ought to be able to get it going again.

---

### Post by imachavel on 2012-01-09
sorry 'places' (next to system right?) seems to have changed in ubuntu, now it's like this:

I have home>boot>grub folder, but really, I don't see log files. I'm really honestly looking for your menu, in (oneiric ocelot)

just don't know where it is, I don't suppose this would help at all?:


[http://www.webupd8.org/2011/09/unity-reboot-ubuntu-unity-launcher-to.html](http://www.webupd8.org/2011/09/unity-reboot-ubuntu-unity-launcher-to.html)

I doubt it, just looks like a menu(interface) changing tool to look prettier and fancier. Give me a second I know you are taking up your whole day(and life) to help me. I want to find that places equivalent in oneiric ocelot, I never used ubuntu prior to natty narwhal btw. Let me see if I can figure this out. To make it worth your time not so you waste your time, I know this forum is a lot to maintain.

---

### Post by imachavel on 2012-01-09
this isn't by some chance similar to what you were directing me towards was it?

cd /boot
ubuntu@ubuntu:/boot$ ls
abi-3.0.0-12-generic     memtest86+_multiboot.bin
config-3.0.0-12-generic  System.map-3.0.0-12-generic
grub                     vmcoreinfo-3.0.0-12-generic
memtest86+.bin
ubuntu@ubuntu:/boot$ 

ok how about this:

cd /home
ubuntu@ubuntu:/home$ cd /boot
ubuntu@ubuntu:/boot$ cd /grub
bash: cd: /grub: No such file or directory
ubuntu@ubuntu:/boot$ 


no such luck? this is bringing me the boot files of the live cd isn't it?? The 288 gb file system is located next to the home folder when I open home it branches out the directories. But I can't cd /288 gb file system. It just won't show me anything. system settings?

---

### Post by imachavel on 2012-01-09
how about this directory?

bin$ ls
autopartition           ip                perform_recipe
autopartition-loop      kbd_mode          pidof
bash                    keyctl            ping
block-attr              kill              ping6
bunzip2                 less              plymouth
busybox                 lessecho          plymouth-upstart-bridge
bzcat                   lessfile          preseed_command
bzcmp                   lesskey           ps
bzdiff                  lesspipe          pwd
bzegrep                 list-devices      rbash
bzexe                   ln                readlink
bzfgrep                 loadkeys          register-module
bzgrep                  login             rm
bzip2                   log-output        rmdir
bzip2recover            lowntfs-3g        rnano
bzless                  ls                run-parts
bzmore                  lsblk             search-path
cat                     lsmod             sed
chacl                   mapdevfs          select_mountoptions
check-missing-firmware  mkdir             select_mountpoint
chgrp                   mknod             setfacl
chmod                   mktemp            setfont
chown                   more              setupcon
chvt                    mount             sh
cp                      mountpoint        sh.distrib
cpio                    mt                sleep
dash                    mt-gnu            static-sh
date                    mv                stty
dbus-cleanup-sockets    nano              su
dbus-daemon             nc                sync
dbus-uuidgen            nc.openbsd        sysfs-update-devnames
dd                      netcat            tailf
debconf-get             netstat           tar
df                      nisdomainname     tempfile
dir                     ntfs-3g           touch
dmesg                   ntfs-3g.probe     true
dnsdomainname           ntfs-3g.secaudit  ulockmgr_server
domainname              ntfs-3g.usermap   umount
dumpkeys                ntfscat           uname
echo                    ntfsck            uncompress
ed                      ntfscluster       unicode_start
egrep                   ntfscmp           update-dev
false                   ntfsdecrypt       user-params
fgconsole               ntfsdump_logfile  vdir
fgrep                   ntfsfix           vmmouse_detect
findmnt                 ntfsinfo          which
fuser                   ntfsls            ypdomainname
fusermount              ntfsmftalloc      zcat
getfacl                 ntfsmove          zcmp
get_mountoptions        ntfstruncate      zdiff
grep                    ntfswipe          zegrep
gunzip                  open              zfgrep
gzexe                   openvt            zforce
gzip                    parted_devices    zgrep
hostname                parted_server     zless
hw-detect               partman           zmore
init-checkconf          partman-command   znew
initctl2dot             partman-commit
in-target               partmap


any of these commands list what you want to see from this directory??

---

### Post by JKyleOKC on 2012-01-09
All these look as if you're getting them from the Live CD rather than the HD. I've never used Unity so can't tell you exactly how to reach a point that lets you examine the HD. Hopefully, OldFred or some of the other members will jump in and tell you how! I'm sure it's simple, but different -- and I use the Xubuntu variant of the distribution, which has a different "places" window, anyway!

You might try "which gigolo" from the command prompt; if it comes back with something like "/usr/bin/gigolo" then you can try a plain "gigolo" command. That should give you a window that shows icons of all the storage devices on your system, including each partition of the hard disk. You can click the icon for the appropriate partition to get a pop-up menu that includes a "Connect" action, and selecting "Connect" should mount that partition and enable the "Open" action that will display the partition's content. At least that's how my copy of Gigolo works, but it's from 2010 and the newer versions may be slightly different. If you get through the "Open" step just copy off the directory names that are displayed and put them in a message together with the name of the partition that contains them.

I don't consider this a waste of my time; I come back to the forum for a break from my other computer tasks (I put together a 40-page quarterly magazine for my school's alumni association, which is tedious detail work scanning photos and doing the page layouts, so I take a break every hour or so). However it's getting close to bedtime here so I probably won't be back onto the thread until tomorrow morning...

---

### Post by topsites on 2012-01-09
Sometimes the only way to diagnose if something's gone bad is to replace it with something that's known to work and although unlikely to fix the problem it may be worth a few minutes of your time to replace the HDD controller cable that goes from the mobo to the HDD or at the very least make sure it is still firmly plugged in, reason I say this is because a loose connection or a cable gone bad could easily result in the trouble you describe... Now if it does not fix the problem then you at least have a spare controller cable that can be used for this very purpose further down the road.

---

### Post by imachavel on 2012-01-10
no I actually took the hd out, connected it with a usb to sata transfer cable, the drive turned on. I then returned it into the external position and reconnected it. I know it works since booting to gparted shows healthy partitions. Thanks though

btw 'gigolo':

gigolo
The program 'gigolo' is currently not installed.  You can install it by typing:
sudo apt-get install gigolo
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install gigolo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gigolo

---

### Post by oldfred on 2012-01-10
You are looking at liveCD. Unbuntu@Ubuntu is liveCD. If in your install after booting you see something like your name and computers name:
fred@fred-LT-A105

Still best to run boot script. It combines multiple commands into one and actually parses some data that is otherwise difficult to get. Just download bootscript in liveCD and run it.

there is a new testing version and you can directly download it, just copy these commands:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by imachavel on 2012-01-10
Boot Info Script 0.60      [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/".


so here:

Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 


this is in the home folder of my live cd though. How do I run it? I'm guessing this download is just to give you more information? I run something at terminal now??

---

### Post by oldfred on 2012-01-10
It does not look like you posted the entire results.txt, but it does show two Linux installs. Ubuntu 11.10 in sda1 and Mint in sda6.  Both show the normal boot files, but the rest of the script would tell more about whether they are correct or not. You have syslinux in MBR & neeed grub2 for one or the other of your installs in the MBR of sda.

You may try this to add grub to MBR:
Boot Repair often fixes minor issues:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This may get you to boot and then you can repair from inside your install.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

Or you can manually reinstall grub2's boot loader to sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR (or use sda6 to directly boot Mint):
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by imachavel on 2012-01-10
that is very descriptive. I'm going to try now. Wish me luck
sorry, another question. I didn't think of it. I have the live cd booted  which is how I am speaking to you now. If I wanted to install to a  flash drive, don't I right click and open archive mounter? doesn't seem  to work. Let me try this:

[http://www.pendrivelinux.com/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/usb-ubuntu-710-gutsy-gibbon-install/)

ok that actually didn't help, except that I resolved that dev/sdc1 is my flash drive, I'm still trying to figure out how to mount dev/sdc1 so that I can install the boot repair disk to the flash drive. Crap. Then I'll continue

---

### Post by imachavel on 2012-01-10
ok I'm a newb, I'm not sure if dev/sdc1 is my flash drive or not. I got this far:

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 003 Device 003: ID 03f0:0d17 Hewlett-Packard LaserJet 1012
Bus 004 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 003 Device 004: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 001 Device 007: ID 0781:5530 SanDisk Corp. Cruzer U3 4gb SDCZ36

still trying to figure out how to mount my flash drive, since I can't burn the boot-repair-disk.iso to a cd, considering that the cd drive is in use, booting the linux live cd. Umm, any ideas? Sorry to newb this up, I see I'm not the only person with grub issues and boot issues on this forum. Wish I was contributing instead of just sucking up space. Anyway, if you can take me any further I'd appreciate it.

---

