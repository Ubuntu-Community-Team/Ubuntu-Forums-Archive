---
title: "GRUB broke, only booting to windows now automatically"
date: 2009-08-27
forum: General Help
---

### Post by domokunrox on 2009-08-27
Out of the blue Windows booted without GRUB prompting me what OS to boot. I just couldn't access Ubuntu. 

So, I pull out this Kubuntu FFawn disk I had lying around to run the console from there and see if I can get GRUB reinstalled once again.

So I 
```
sudo grub
find /boot/grub/stage1
``` and I get
"Error 15: file not found"

Here are the results of sudo fdisk -lu

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976751999   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63       16064        8001    7  HPFS/NTFS
/dev/sdb2           16065   488392064   244188000   83  Linux
ubuntu@ubuntu:~$

```

*sigh* Lost here, not a advanced Linux user at all, so I appreciate the help. Thanks.

---

### Post by bchurchill on 2009-08-27
First things first:  reboot and look for a chance to get into GRUB.  Either a different bootloader is running, and you'll need to reinstall GRUB, or GRUB is configured wrong.  In the first case you'll need to reinstall grub ([https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows]("https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows")).  Otherwise, follow instructions below.


EDIT: upon rereading your post, it now seems that grub is probably gone, so the instructions below won't be needed in all likelyhood, unless you have trouble with grub afterward.

Next, if this doesn't work:

Can you boot using a live cd, mount your hard drive and post the conents of 

ls /boot

and

ls /boot/grub

and

cat /boot/grub/menu.lst

Then we'll work this all out.  :)

---

### Post by domokunrox on 2009-08-27
```
ubuntu@ubuntu:~$ ls /boot
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic
ubuntu@ubuntu:~$ ls /boot/grub
ls: /boot/grub: No such file or directory
ubuntu@ubuntu:~$

```

---

### Post by Vince N on 2009-08-27
This happens to me occasionally when my Windows XP install gets hosed.  When you reinstall Windows it overwrites grub.

I find a utility called "Super Grub Disk" is very useful in this case because it will scan your drives and rebuild grub from scratch.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by bchurchill on 2009-08-27
Yeah, you'll need to reinstall grub with the link above.  And if you're still having issues, follow the second set of instructions again.

---

### Post by domokunrox on 2009-08-27
> **Vince N said:**
> This happens to me occasionally when my Windows XP install gets hosed.  When you reinstall Windows it overwrites grub.

I find a utility called "Super Grub Disk" is very useful in this case because it will scan your drives and rebuild grub from scratch.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I've seen that before and it looks helpful, but how do I use it?

EDIT: For the record, I didn't install any OS and create this problem. I was living in great Ubuntu/Windows harmony on 2 seperate hard drives.

---

### Post by domokunrox on 2009-08-27
Tried using Super GRUB disk. Didn't work.

I got auto super grub disk 1.7 and it'll restart the computer but it'll still boot to windows automatically.

Any other suggestions?

---

### Post by bchurchill on 2009-08-27
Install grub using the link above.  As long as /boot/grub doesn't exist and you want it back, this is the task at hand.

([https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows))

---

### Post by domokunrox on 2009-08-27
So, let me get this straight because I don't want to screw up any of my installations.

I'm going to do it exactly like this?

```
sudo grub

```

Then I'm going to do 
```
root (hdA,B)
```

Where is A....1 and B is.....2?

I really don't understand the simple yet so confusing number and letter system that is going on here. Can anyone clarify?

---

### Post by bchurchill on 2009-08-27
Sorry there weren't enough details, let me explain.  (This probably won't mess up the partitions themselves even if the values were wrong, because grub will complain). 

Grub numbers its partitions and hard drives starting at zero.  So based on your fdisk output, you have two hard drives, and the second one is the one with linux, so yes, A = 1.  While your partition is /dev/sdb2, grub calls this partition #1 (partition #0 is /dev/sdb1).  So you'll issue

root (hd1,1) 

The setup command has more flexibility.  It specified which disk the master boot record is located on, and since you have two HDDs, you get to choose.

You're probably going to want to do

setup (hd0)

I've never actually tried installing grub on one disk and starting kernels on another, but it should work fine.  Then when you boot up BIOS will automatically pick the first hard drive, start GRUB, and then choose your O/S (windows1, windows2, or linux)

However, you can also do

setup (hd1)

This way when you bootup in BIOS, you'll chose either your first hard drive (with two Windows installations and another bootloader you'll need to install separately) or boot to your second hard drive (with Linux and GRUB)

Note that with either option Windows may not appear on the GRUB lists at first.  Then we'd go edit (hd1,1)/boot/grub/menu.lst.

---

### Post by domokunrox on 2009-08-27
I see, well, when I installed Ubuntu right after I installed Windows it was very strongly opposing that the MBR be on the another hard drive aside from the one that has the primary partition (Ubuntu). It was pretty much like...No, and I was like, Ok, thats fine. 

Anyway, over time my GRUB menu started expanding with more Ubuntu options. It began to get annoying and I didn't understand why. Thats actually been a secondary question I was going to ask. Going to reboot this thing and try to fix it, brb.

---

### Post by domokunrox on 2009-08-27
Nope, we hit a new snag here

```
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type
```

---

### Post by bchurchill on 2009-08-27
> **domokunrox said:**
> Nope, we hit a new snag here

```
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type
```

Oops, it looks like I was wrong.  You can't install GRUB to the other HD because it really wants an EXT3 (not NTFS) partition for that.  So you'll just do setup (hd1) next time.  You can setup BIOS to go to hd1 by default.

As for the extra Ubuntu entries, that happens when the kernel gets updated.  If you're short on space, you can remove the extra kernels with synnaptic.  I wouldn't do that (people have messed up before).  Instead, edit /boot/menu.lst once grub has been installed and find the options line that says something like

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

and change 

# howmany=all

to

# howmany=2

(NOTE: don't uncomment it).
or any value you want.  This will give you 4 ubuntu listings: 2 kernels, and recovery modes for each.  You can specify more or less, although I wouldn't try removing the recovery modes.

Then run sudo update-grub.  This will update the automatically generated list, and next time you get a kernel update it won't list too many.

---

### Post by domokunrox on 2009-08-27
Nope, no dice there

```
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type

```

---

### Post by mike555 on 2009-08-27
Have you thought about a different free boot manager? I found that "GAG" works good for me ... [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by bchurchill on 2009-08-27
Huh.  I really don't know what's going on then.  You used sudo grub, right?  You can try another bootloader, like LILO, but I really have no experience with that.  You could try googling around for the "Error 2: Bad file...".  

An important thing to check is that grub can actually read stuff.  From the grub shell try typing 

root (hd1,1)/

and then press TAB, not enter.  GRUB should list all the files in the root of that partition.  If not, something is wrong with the partition itself.  In particular, error 22 or error 21 means something is missing, and you should

fdisk -l

and 

ls -l /dev | grep -e sd.*

---

### Post by domokunrox on 2009-08-27
> **mike555 said:**
> Have you thought about a different free boot manager? I found that "GAG" works good for me ... [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

I've thought about doing a lot of things for my OS booting options. Even paying for Boot Manager software. I just can't quite justify it, yet. Perhaps when someone can guide me how to to make a MacOSX 10.4 hackitosh, I will. Thanks for the plug though.

---

### Post by domokunrox on 2009-08-27
> **bchurchill said:**
> Huh.  I really don't know what's going on then.  You used sudo grub, right?  You can try another bootloader, like LILO, but I really have no experience with that.  You could try googling around for the "Error 2: Bad file...".  

An important thing to check is that grub can actually read stuff.  From the grub shell try typing 

root (hd1,1)/

and then press TAB, not enter.  GRUB should list all the files in the root of that partition.  If not, something is wrong with the partition itself.  In particular, error 22 or error 21 means something is missing, and you should

fdisk -l

and 

ls -l /dev | grep -e sd.*

Here is the result of those two commands

```
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7872     2015216    b  W95 FAT32
ubuntu@ubuntu:~$ ls -l /dev | grep -e ds.*
crw-rw---- 1 root   audio    14,  12 2009-08-27 16:22 adsp
crw-rw---- 1 root   audio    14,   3 2009-08-27 16:22 dsp
lrwxrwxrwx 1 root   root          24 2009-08-27 16:22 sndstat -> /proc/asound/oss/sndstat

```

Weird, I know.

---

### Post by Vince N on 2009-08-27
Looks like the other folks have the GRUB issue well in hand so I just wanted to address this issue here for you.

> **domokunrox said:**
> 

Anyway, over time my GRUB menu started expanding with more Ubuntu options. It began to get annoying and I didn't understand why. Thats actually been a secondary question I was going to ask. Going to reboot this thing and try to fix it, brb.

Ubuntu often times updates the OS Kernel in order to add certian features, fix bugs, add better hardware support however even in the best case scenario sometimes it might break something that worked fine for you before leaving your system unbootable  In order to prevent this whenever the Kernel updates rather than replacing your existing Ubuntu Entry it simply creates new one in addition to the one you had before.  This way if the new kernel does not work for you you can easily select the old one that did and decide what you want to do from there.

If you get too many of these update you can open /boot/grub/menu.lst and comment out the older entries by adding a "#" before their menu entries like so....

```

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        c8638cf5-529e-428c-b4c9-2ec257cce8c9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c8638cf5-529e-428c-b4c9-2ec257cce8c9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        c8638cf5-529e-428c-b4c9-2ec257cce8c9
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c8638cf5-529e-428c-b4c9-2ec257cce8c9 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

#title        Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid        c8638cf5-529e-428c-b4c9-2ec257cce8c9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c8638cf5-529e-428c-b4c9-2ec257cce8c9 ro quiet splash 
#initrd        /boot/initrd.img-2.6.28-11-generic
#quiet

#title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid        c8638cf5-529e-428c-b4c9-2ec257cce8c9
#kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c8638cf5-529e-428c-b4c9-2ec257cce8c9 ro  single
#initrd        /boot/initrd.img-2.6.28-11-generic

#title        Ubuntu 9.04, memtest86+
#uuid        c8638cf5-529e-428c-b4c9-2ec257cce8c9
#kernel        /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


```

And then if you ever need to access them just uncomment them and you can again select them from GRUB.

---

### Post by bchurchill on 2009-08-27
> **domokunrox said:**
> 

```
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7872     2015216    b  W95 FAT32
ubuntu@ubuntu:~$ ls -l /dev | grep -e ds.*
crw-rw---- 1 root   audio    14,  12 2009-08-27 16:22 adsp
crw-rw---- 1 root   audio    14,   3 2009-08-27 16:22 dsp
lrwxrwxrwx 1 root   root          24 2009-08-27 16:22 sndstat -> /proc/asound/oss/sndstat

```

Fortunately, there's a typo here and your hard drives haven't disappeared.  it's | grep -e sd.*, rather than | grep -e ds.*

This does point out that only your third (?) hard drive is being found, and it's a FAT32.  So for some reason it's not seeing the other(s?).  Um... try

fdisk -l /sda
fdisk -l /sdb
fdisk -l /sdc

I'm not sure... maybe fdisk is only showing one.  The man page seems to indicate it gets it list of devices from some file, which may not be adequite from the livecd.

Did you try the GRUB commands?  What happened then?

@VinceN:  The only downside of removing kernels from the list that way is the kernel list will be regenerated every time a new one is installed.  If you modify the parameter on the number of kernels to automatically generate, that value will be respected every time the list is regenerated so you don't have to do extra work to comment them out again.

---

### Post by Vince N on 2009-08-27
This is true, However I like to keep only one version of Ubuntu showing but I'd rather have the update bomb and still have an easy backup rather than have to go back to terminal to get everything back agian.  Kernel updates only happen every so often however so I don't mind the 2 seconds it takes to tweak it when it does update anyway.

> @VinceN:  The only downside of removing kernels from the list that way is the kernel list will be regenerated every time a new one is installed.  If you modify the parameter on the number of kernels to automatically generate, that value will be respected every time the list is regenerated so you don't have to do extra work to comment them out again.


---

### Post by louieb on 2009-08-27
Need a look at your system setup. Please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt  in your next post.

---

### Post by domokunrox on 2009-08-27
You're right, typo. Sorry.

```
crw-rw-rw- 1 root   tty       2,  61 2009-08-27 16:20 ptysd
brw-rw---- 1 root   disk      8,   0 2009-08-27 16:20 sda
brw-rw---- 1 root   disk      8,   1 2009-08-27 16:20 sda1
brw-rw---- 1 root   disk      8,  16 2009-08-27 16:20 sdb
brw-rw---- 1 root   disk      8,  17 2009-08-27 16:20 sdb1
brw-rw---- 1 root   disk      8,  18 2009-08-27 16:20 sdb2
brw-rw---- 1 root   plugdev   8,  32 2009-08-27 16:20 sdc
brw-rw---- 1 root   plugdev   8,  33 2009-08-27 16:20 sdc1
crw-rw-rw- 1 root   tty       3,  61 2009-08-27 16:20 ttysd

```

---

### Post by domokunrox on 2009-08-27
> **louieb said:**
> Need a look at your system setup. Please follow the [Boot Info Script Instructions]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and put the results.txt  in your next post.

Unfortunatly I don't have a Ubuntu Live CD at my disposal.

I do have a Kubuntu Feisty Fawn Disto Live CD though that I am using.

is there a way to do this info script on that?

---

### Post by domokunrox on 2009-08-27
> **bchurchill said:**
> Did you try the GRUB commands?  What happened then?


You're talking about the TAB instead of enter, correct?

Yeah, pressing TAB didn't do anything

Forgot to mention it, sorry.

---

### Post by louieb on 2009-08-28
> **domokunrox said:**
> I do have a Kubuntu Feisty Fawn Disto Live CD though that I am using.
That will work. As will almost any other Linux live CD.

---

### Post by domokunrox on 2009-09-02
I'm still having trouble. Here is my attempt at installing grub again and here is my attempt at a boot info script that I can't get working

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ $ grub
bash: $: command not found
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find/boot/grub/stage1
find/boot/grub/stage1

Error 27: Unrecognized command
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub>
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           1        8001    7  HPFS/NTFS
/dev/sdb2               2       30401   244188000   83  Linux
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd1,1)
root (hd1,1)
grub> setup (hd1)
setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type
grub>
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$      
```

---

### Post by domokunrox on 2009-09-02
Really do need the help.

---

### Post by domokunrox on 2009-09-02
Got the script to work. A SINGLE space stoped the script from working properly.

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hdc
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: hdc ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 732 MB, 732921856 bytes
255 heads, 63 sectors/track, 22 cylinders, total 357872 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63        16,064        16,002   7 HPFS/NTFS
/dev/sdb2              16,065   488,392,064   488,376,000  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: TYPE="ntfs" 
/dev/sdb1: TYPE="ntfs" 
/dev/sdb2: UUID="31e43d63-289c-473e-b451-29de4aa0a3e2" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


================================ sda1/boot.ini: ================================


C:\ubnldr.mbr="Auto Super Grub Disk"

================================ sda1/BOOT.INI: ================================


C:\ubnldr.mbr="Auto Super Grub Disk"

================================ sdb1/boot.ini: ================================

[boot loader]
;timeout=1
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
;
[spybotsd]
timeout.old=1


=========================== sdb2/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=31e43d63-289c-473e-b451-29de4aa0a3e2

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
# defoptions=quiet splash

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
# howmany=all

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
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, memtest86+
uuid		31e43d63-289c-473e-b451-29de4aa0a3e2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=31e43d63-289c-473e-b451-29de4aa0a3e2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 176.5GB: boot/grub/menu.lst
 176.5GB: boot/grub/stage2
 176.5GB: boot/initrd.img-2.6.27-11-generic
 176.6GB: boot/initrd.img-2.6.28-11-generic
 176.5GB: boot/initrd.img-2.6.28-13-generic
 176.5GB: boot/initrd.img-2.6.28-14-generic
 176.6GB: boot/initrd.img-2.6.28-15-generic
 176.5GB: boot/vmlinuz-2.6.27-11-generic
 176.5GB: boot/vmlinuz-2.6.28-11-generic
 176.5GB: boot/vmlinuz-2.6.28-13-generic
 176.5GB: boot/vmlinuz-2.6.28-14-generic
 176.6GB: boot/vmlinuz-2.6.28-15-generic
 176.6GB: initrd.img
 176.5GB: initrd.img.old
 176.6GB: vmlinuz
 176.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 77 c4 6d 00 00 00  |.......|..w.m...|
000001b0  00 00 81 00 00 c9 0e 00  9b 3b 9b 3b 08 7b 80 01  |.........;.;.{..|
000001c0  01 00 07 fe 3f 00 3f 00  00 00 82 3e 00 00 00 00  |....?.?....>....|
000001d0  01 01 83 fe ff ff c1 3e  00 00 c0 06 1c 1d 00 00  |.......>........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

