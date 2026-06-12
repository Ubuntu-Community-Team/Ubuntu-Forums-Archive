---
title: "How to break GRUB in 30 seconds (or, why you shouldn't delete partitions) -- help!"
date: 2009-10-23
forum: General Help
---

### Post by emmiesix on 2009-10-23
SUMMARY:  I get "Grub loading... Error 15" (no menu, nothing after) when trying to booth up.

History:

I recently installed 9.04 64 bit on a brand new Dell.  Feeling optimistic about my linux skills, I decided to put different important things on their own partitions.  This has turned out to be a major headache because (despite efforts) I did a really bad job of estimating how much size certain things need.

I was running out of room on /var (couldn't update to the new beta of 9.10) so I decided to remove the partition and return var to it's natural home on /.  I booted up using a live USB (with mint 7), and copied the contents of var, using this command (roughly):

sudo cp -d -r -p -v /media/diskwithvar/* /media/diskwithroot/tvar/

I would think that would keep all the permissions and links as desired.  I checked the size and number of files and all looked good. 

I then used gparted to delete the 2 GB var partition (I'm sure this was done correctly, as it is now gone!).  I fear my mistake might have been to grow a nearby media folder to take up the extra 2 GB.  Not sure.

I'm using ext4 by the way -- I know there are some issues with it, I hope that is not my problem.

I have been trying to troubleshoot, but with such scanty error information I have NO IDEA what grub is looking for and can't find.  I don't see a grub.conf anywhere.  I have messed with fstab and menu.lst some, but since a menu never comes up I'm not sure if menu is the problem at all.  Is there a way to see the drives being mounted?  I'd like to know that it's working there first.  Here are the files:

```
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
timeout		5

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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root (hd0,6)
kernel		/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash 
initrd		/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root (hd0,6)
kernel		/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro  single
initrd		/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-15-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro quiet splash 
initrd		/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-15-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro  single
initrd		/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-14-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro quiet splash 
initrd		/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-14-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro  single
initrd		/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-13-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro quiet splash 
initrd		/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-13-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro  single
initrd		/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-11-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/vmlinuz-2.6.28-11-generic root=UUID=f965dbfa-58c4-4804-ac8b-76cac8438dd5 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		d17558a6-8d1f-4073-b40f-765053d1267c
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
/dev/sda1 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda8 during installation
/dev/sda7 /boot           ext4    relatime        0       2
# /home was on /dev/sda3 during installation
/dev/sda3 /home           ext4    relatime        0       2
# /media/shared was on /dev/sda4 during installation
/dev/sda4 /media/shared   ext4    relatime        0       2
# /opt was on /dev/sda9 during installation
/dev/sda8 /opt            ext4    relatime        0       2
# /root was on /dev/sda10 during installation
/dev/sda9 /root           ext4    relatime        0       2
# /tmp was on /dev/sda7 during installation
#UUID=0def9816-33d4-46d2-a921-388c9392c140 /tmp            ext4    relatime     \  #0       2
# /usr was on /dev/sda5 during installation
/dev/sda5 /usr            ext4    relatime        0       2
# /var was on /dev/sda6 during installation
#UUID=c9246bfb-dd90-4b06-b2e2-5195a0ff3ab9 /var            ext4    relatime        #0       2
# swap was on /dev/sda11 during installation
/dev/sda10 none            swap    sw              0       0
/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0
```

---

### Post by emmiesix on 2009-10-23
I'd post the results of df as well, but that is useless when in live-usb.  

But, I have figured out what should be mounted where using gparted:

sda1 - /root   ~12 G
sda2 - logical containing:
   sda10 - swap  ~8 G
   sda5 - /usr   ~12 G
   sda6 - formerly /tmp, now not mounted (hopefully) as it's too small
   sda7 - /boot  ~500 M
   sda8 - /opt  ~9 G
   sda9 - /root ~250 M
sda3 - /home  ~75 G
sda4 - /media/shared ~ 400 GB

~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Lastly, I am obviously a noob, but I thought the file permissions were a bit odd, when I checked the mounted disks under the live-key:

drwxr-xr-x 23 root root  4.0K 2009-10-23 02:42 disk-2
drwx------ 23 root root  1.0K 2009-10-22 16:47 disk-3
drwxr-xr-x  4 root root  3.0K 2009-10-22 15:43 disk
drwxr-xr-x 12 1000 users 4.0K 2009-10-22 04:20 disk-7
drwxr-xr-x 22 root root  4.0K 2009-09-30 12:50 disk-4
drwxr-xr-x  4 root root  4.0K 2009-08-27 07:06 disk-6
drwxrwxrwt 16 root root  9.0K 2009-08-27 06:58 disk-5
drwxr-xr-x 15 root root  4.0K 2009-08-26 05:50 disk-1
mint@mint /media $ 


disk-3 corresponds to  /root (as expected), but shouldn't boot (disk) have full permissions like the former tmp (disk-5) ??

---

### Post by gareththegeek on 2009-10-23
> title		Ubuntu 9.04, kernel 2.6.28-16-generic
root (hd0,6)
kernel		/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash 
initrd		/initrd.img-2.6.28-16-generic
quiet

root (hd0,6) here refers to the 0th (i.e. first) ide disk and the 6th (i.e. seventh partition.

Could it be that you have moved the root parition so it is no longer seventh?

When you are on the grub boot menu you can edit the entries by pressing 'e'

---

### Post by P4man on 2009-10-23
[COLOR="Silver"]You have 10 partitions on that drive while the limit afaik is 4. If you need more than 4 you have to make an extended partition (which counts as 1 of those 4) and inside that you can make as many logical partitions as you want. Perhaps you did that, but I cant tell from the output you gave
[/COLOR]
edit: ignore. you call it "logical" but im sure you did it right

Secondly, assuming the above is okay, did you just try installing grub?

---

### Post by alphaniner on 2009-10-23
Error 15 means GRUB is not finding the kernel file.  If /var was on sda6 which you deleted, then sda7 is now the 6th partition rather than the 7th.  Which means your settings in menu.list are probably incorrect.  Everywhere it references **hd(0,6)** should now be **hd(0,5)** (numbering starts from 0, so hd(0,5) is the first drive, 6th partition).  Run

> sudo grub-install /dev/sda7

---

### Post by P4man on 2009-10-23
> **gareththegeek said:**
> root (hd0,6) here refers to the 0th (i.e. first) ide disk and the 6th (i.e. seventh partition.

Could it be that you have moved the root parition so it is no longer seventh?


Bingo. Its his /boot partition which has changed numbers. *root (hdx,x)* should point to the partition where grub is, presumable /boot.

---

### Post by emmiesix on 2009-10-23
> **gareththegeek said:**
> root (hd0,6) here refers to the 0th (i.e. first) ide disk and the 6th (i.e. seventh partition.

Could it be that you have moved the root parition so it is no longer seventh?

When you are on the grub boot menu you can edit the entries by pressing 'e'

Well, I never get to the grub menu proper, that's what is odd.  I have tried pressing 'esc' after the Error 15 but I don't get anything.

Also, I have completely re-written the fstab and menu.lst.  Before, everything was by UUID which I found incredibly hard to read, so I have changed everything to the partition names.  I assume this is ok?  In any case, I'm sure that boot is now on /dev/sda7 (if you look at my fstab, you can see that the installer conveniently added the comment that /boot was on sda8 during installation.  I deleted partition sda6 when removing var, so that is correct in being (hda0,6)).

> 
edit: ignore. you call it "logical" but im sure you did it right

Sorry, some formatting got lost.  Obviously sda1 - sda4 are primary partitions, and everything below sda2 belongs as a part of it.  I thought those were called "logical" partitions, but maybe it's the sub-partitions that are logical.  


Thanks for the quick replies, but unfortunately I believe my menu.lst correctly points to the the /boot partition.  Any other ideas??

---

### Post by emmiesix on 2009-10-23
> **alphaniner said:**
> Error 15 means GRUB is not finding the kernel file.  If /var was on sda6 which you deleted, then sda7 is now the 6th partition rather than the 7th.  Which means your settings in menu.list are probably incorrect.  Everywhere it references **hd(0,6)** should now be **hd(0,5)** (numbering starts from 0, so hd(0,5) is the first drive, 6th partition).  Run

I have refuted the incorrect partition bit, but I would be willing to try reinstalling grub if that is quicker than troubleshooting.  I thought you had to be mounted on your local filesystem, though... and I assume I would want to run sudo grub-install /dev/sda7 only if that partition were in fact the boot dir (not as you claim, otherwise, I would be installing over god knows what??)

---

### Post by alphaniner on 2009-10-23
Yeah, I think you're right about the command not being appropriate in your case.  Good catch.  You should be able to use the command but the syntax I provided is wrong.  I've never used it with a separate /boot.  There is some stuff about that [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Also, there is a good reason for using UUIDs in fstab.  I know it's ugly, but the /dev/sdX# method has limitations that are overcome by UUID.

---

### Post by P4man on 2009-10-23
> **emmiesix said:**
> I have refuted the incorrect partition bit, but I would be willing to try reinstalling grub if that is quicker than troubleshooting.  I thought you had to be mounted on your local filesystem, though... and I assume I would want to run sudo grub-install /dev/sda7 only if that partition were in fact the boot dir (not as you claim, otherwise, I would be installing over god knows what??)

can you verify that /boot partition actually contains grub and your kernels?

As for running grub setup, I understand what you're saying, but it did work from a live cd each time I tried it. It seems to ignore the livecd filesystem so its not adding those to your grub or anything. But the safest way to do it I suppose would be to chroot into your existing install. have a look here:

[http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot](http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot)

---

### Post by emmiesix on 2009-10-23
thanks alphaniner.  So does anything else stand out about the fstab?  That is what I am concerned about most.

Does anyone know of a way to see GRUB mount (or fail to) the partitions?  It seems like it should only need / and /boot ?

Should I switch everything back to UUID?

---

### Post by P4man on 2009-10-23
check my previous post if you missed it. But your problem at this point is not fstab. You're not getting far enough in the boot process that fstab would even be processed.

---

### Post by emmiesix on 2009-10-23
> **P4man said:**
> can you verify that /boot partition actually contains grub and your kernels?

As for running grub setup, I understand what you're saying, but it did work from a live cd each time I tried it. It seems to ignore the livecd filesystem so its not adding those to your grub or anything. But the safest way to do it I suppose would be to chroot into your existing install. have a look here:

[http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot](http://developer.spikesource.com/wiki/index.php/Article:Ubuntu_how_to_re-install_grub_using_chroot)

Everything appears to be good:

```
mint@mint /media $ cd disk
mint@mint /media/disk $ ls
abi-2.6.28-11-generic         memtest86+.bin
abi-2.6.28-13-generic         System.map-2.6.28-11-generic
abi-2.6.28-14-generic         System.map-2.6.28-13-generic
abi-2.6.28-15-generic         System.map-2.6.28-14-generic
abi-2.6.28-16-generic         System.map-2.6.28-15-generic
config-2.6.28-11-generic      System.map-2.6.28-16-generic
config-2.6.28-13-generic      vmcoreinfo-2.6.28-11-generic
config-2.6.28-14-generic      vmcoreinfo-2.6.28-13-generic
config-2.6.28-15-generic      vmcoreinfo-2.6.28-14-generic
config-2.6.28-16-generic      vmcoreinfo-2.6.28-15-generic
grub                          vmcoreinfo-2.6.28-16-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-13-generic
initrd.img-2.6.28-14-generic  vmlinuz-2.6.28-14-generic
initrd.img-2.6.28-15-generic  vmlinuz-2.6.28-15-generic
initrd.img-2.6.28-16-generic  vmlinuz-2.6.28-16-generic
lost+found
mint@mint /media/disk $ 

```

---

### Post by alphaniner on 2009-10-23
Could you do a simple **fdisk -l**?

---

### Post by P4man on 2009-10-23
Good. Then the chroot / grub install will probably fix it. Sounds like your more than knowledgeable enough that you can adjust the commands there to suit your situation.

---

### Post by emmiesix on 2009-10-23
> **alphaniner said:**
> Could you do a simple **fdisk -l**?

Can do.  Though, I definitely don't know what that means:
```

mint@mint /media/disk $ fdisk -l

Disk /dev/sdc: 1015 MB, 1015021568 bytes
65 heads, 32 sectors/track, 953 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0x0004e22a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         942      978928    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 64, 32) logical=(941, 18, 32)
mint@mint /media/disk $ 


```
Different physical/logical endings bad, I would think??

EDIT:  Uh, this is probably my 1GB usb key with Mint on it.  So maybe not helpful.

---

### Post by alphaniner on 2009-10-23
Sorry, you probably need to use sudo with the command.  But don't worry about it, it seems like you're in the right track with chroot.

---

### Post by emmiesix on 2009-10-23
New problem:


```
chroot: cannot run command `/bin/bash': Exec format error

```

Apparently this is because I've got 32-bit Mint on the usb (it was from an install on an old laptop) and the current laptop is 64-bit.  So I'm off to change the live-key to a 64-bit version.  I like to keep these threads updated for future noob reference.  will report back.

---

### Post by P4man on 2009-10-23
> **emmiesix said:**
> New problem:
 I like to keep these threads updated for future noob reference.  

A noob is someone asking how to turn the pc off or where the start button is. If you're noob then allmost everyone posting here is. FWIW, I think it took me 2 years before I dared separating my /home partition.

---

### Post by emmiesix on 2009-10-23
Ok, I may not be new but I only have 1/2 a clue which can be twice as dangerous... :)


The good news is that I (we) fixed the problem!!

As is typical, I'm not sure exactly what fixed it.  I went into grub, tried to get the find /boot/grub/stage1 and failed several times before just saying screw it and copied that particular file from /usr/lib/grub/ ... and then it worked with the command 

grub> setup (hd0)

A few other difficulties:  I had to specifically mount the ext4 type, 

mount -t ext4 /dev/sda7 /mnt/boot  ... etc

and I ended up mounting /usr and /root as well since they are on their own partitions.  I was getting errors without them, though I'm not 100% sure it was necessary to the final solution.

Thanks guys!

---

### Post by richlyn9 on 2010-02-19
I updated  my lucid alpha testing install after which I am unable to boot into any of my Ubuntu installs(sda11 has a dedicated Burg partition and sda10 has the stable karmic install and sda9 has the testing lucid install)
Now I am trying to recover (rewrite Burg or atleast grub2 on the MBR) my installs 
This is what happens
custom@custom:~$ sudo mount /dev/sda10 /mnt
custom@custom:~$ sudo mount -o bind /dev /mnt/dev
custom@custom:~$ chroot/mnt
bash: chroot/mnt: No such file or directory
custom@custom:~$ chroot /mnt
chroot: cannot change root directory to /mnt: Operation not permitted
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$ 

i tried a slightly different code
with little sucess

custom@custom:~$ sudo mount /dev/sda10 /mnt
mount: /dev/sda10 already mounted or /mnt busy
mount: according to mtab, /dev/sda10 is already mounted on /mnt
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error
custom@custom:~$


custom@custom:~$ whereis sh
sh: /bin/sh /bin/sh.distrib /usr/share/man/man1/sh.1.gz
custom@custom:~$ whereis chroot
chroot: /usr/sbin/chroot /usr/share/man/man8/chroot.8.gz
custom@custom:~$ whereis dash
dash: /bin/dash /usr/share/man/man1/dash.1.gz

I also ran a whereis for bash and it also is there

---

