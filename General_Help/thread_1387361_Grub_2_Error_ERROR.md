---
title: "Grub 2 Error: ERROR:"
date: 2010-01-21
forum: General Help
---

### Post by ApocoLypTus on 2010-01-21
GNU GRUB Version 1.97~beta4
 
[ Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB lists possible device/file completions. ]
 
sh:grub> 
 
I shut down my computer. (64bit) With Kubuntu 9.10 Karmic Koala. I was dual booting it with Windows Vista. All was working good untill one night i shut it down, it came up with that error.
 
I am a TOTAL newbie to Kubuntu. I need a fix :(, Please help.
 
I cannot go into my bootloader loading Windows Vista OR Karmic. I have googled this and there has been no fix that works for me.

---

### Post by ApocoLypTus on 2010-01-21
I need help please...

---

### Post by john newbuntu on 2010-01-21
Please follow step 15 from:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ranch hand on 2010-01-21
I think that you need to follow these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

ignoring the directions for file editing as you should not need it.

This is probably a case of MS not playing nice with others.  If that does not work and you get no inspiration from the link in the last post or the link in my sig, post back and we will see what we can do wit ha little more info from you.

---

### Post by ApocoLypTus on 2010-01-22
> **john newbuntu said:**
> Please follow step 15 from:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> **ranch hand said:**
> I think that you need to follow these directions;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

ignoring the directions for file editing as you should not need it.

This is probably a case of MS not playing nice with others.  If that does not work and you get no inspiration from the link in the last post or the link in my sig, post back and we will see what we can do wit ha little more info from you.

Okay i will do What both of you said. I will try to do it right, but i dont know anything about it, I will keep you updated. I have to go to school, i will work on it after.

---

### Post by ApocoLypTus on 2010-01-22
> **ApocoLypTus said:**
> Okay i will do What both of you said. I will try to do it right, but i dont know anything about it, I will keep you updated. I have to go to school, i will work on it after.
 
I was following step 15 perfectly untill i got up to the 
 
**insmod /boot/grub/_linux.mod **but when i did the command it said 
 
error: file not found
sh:grub>
 
i dont know what to do now.

---

### Post by ranch hand on 2010-01-22
I am not sure which of drs305's directions you are following.

I think that restoring the bugger to the mbr should have done it.  Did you try that first?

---

### Post by ApocoLypTus on 2010-01-22
> **ranch hand said:**
> I am not sure which of drs305's directions you are following.
 
I think that restoring the bugger to the mbr should have done it. Did you try that first?
 
Im sorry.. But i do not know what you just said.. Im really noobie and i do not know what that means. drs305? i was following john newbuntus link that he gave me. 
 
What should i do now? in newbie termms.

---

### Post by ranch hand on 2010-01-22
drs305 is the guy that wrote the;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

How To

I am hoping that you tried;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

first because that is, I think, all that was wrong with your system.  Someimes you can screw things worse by doing un-needed things.

That is why I would like to knwo which of hes instructions you were following.  To see if they are what you need and if they could cause a problem.

It is always good when trying to get something straightened out to know what has been done already.

---

### Post by ApocoLypTus on 2010-01-22
> **ranch hand said:**
> drs305 is the guy that wrote the;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

How To

I am hoping that you tried;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

first because that is, I think, all that was wrong with your system.  Someimes you can screw things worse by doing un-needed things.

That is why I would like to knwo which of hes instructions you were following.  To see if they are what you need and if they could cause a problem.

It is always good when trying to get something straightened out to know what has been done already.

When i went to drs305's guide, i tried number 15. But when i did that i got a error: File not found. while doing the insmod /boot/grub/_linux.mod step. It didn't work.

And for the other link that you gave me. I didn't know what to start with. ([https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)) So i didn't bother with that... I think that was a mistake and can you tell me what i should do on the wiki.

---

### Post by c0mput3r_n3rD on 2010-01-22
Try burning GRUB Bootloader to a cd and booting with that.  You should be able to select ubuntu or windows as long as the partition(s) hasn't been deleted.

---

### Post by ApocoLypTus on 2010-01-22
> **c0mput3r_n3rD said:**
> Try burning GRUB Bootloader to a cd and booting with that.  You should be able to select ubuntu or windows as long as the partition(s) hasn't been deleted.

Okay. But where is the grub stuff? i cant even get onto my computer with the GRUB already on it. Do i have to download something? Then Burn it to a disk? And can you tell me how to do that?

---

### Post by c0mput3r_n3rD on 2010-01-22
> **ApocoLypTus said:**
> Okay. But where is the grub stuff? i cant even get onto my computer with the GRUB already on it. Do i have to download something? Then Burn it to a disk? And can you tell me how to do that?


Yes you have to download the .iso, and burn the image to a disk (same as burning a copy of ubuntu to a cd). The link is [here]("ftp://alpha.gnu.org/gnu/grub/"), download one of the .tar.gz files (doesn't really matter which one, just different versions which is listed as part of the name) Hope this helps!

---

### Post by ApocoLypTus on 2010-01-22
> **c0mput3r_n3rD said:**
> Yes you have to download the .iso, and burn the image to a disk (same as burning a copy of ubuntu to a cd). The link is [here]("ftp://alpha.gnu.org/gnu/grub/"), download one of the .tar.gz files (doesn't really matter which one, just different versions which is listed as part of the name) Hope this helps!

So all i have to do Is download it, Burn it to disk iso. Then just put it into my dvd drive in my gimped computer. It will come up with Grub2 or Grub? and will it come up automatically? And will i have to do more after?

---

### Post by c0mput3r_n3rD on 2010-01-22
> **ApocoLypTus said:**
> So all i have to do Is download it, Burn it to disk iso. Then just put it into my dvd drive in my gimped computer. It will come up with Grub2 or Grub? and will it come up automatically? And will i have to do more after?


Well you have to boot from the CD/DVD, and then it'll show you the same thing as the normal grub bootloader (downloaded on your HDD when you install ubuntu), and you will be able to pick the partition you want to boot from... Hopefully  :)  Try it out tell me what happens.

---

### Post by ApocoLypTus on 2010-01-22
> **c0mput3r_n3rD said:**
> Well you have to boot from the CD/DVD, and then it'll show you the same thing as the normal grub bootloader (downloaded on your HDD when you install ubuntu), and you will be able to pick the partition you want to boot from... Hopefully  :)  Try it out tell me what happens.

Okay i will. But i will do it tomorrow because i am busy tonight. I will burn this disk image then i will insert it into my disk drive. If there is an easier way to do this it would be greatly appreciated. I would just liek to do some stuff on the grub recovery thing but nothing has worked.

---

### Post by ranch hand on 2010-01-22
You can try the above method.  Could be a great thing.  Haven't ever seen it.

If it works and you boot to the offending OS you will need to run;
```

sudo update-grub

```
and then;
```

sudo grub-install /dev/sda

```
editing the "sda" to suit the needs of your box.

If you do not boot to the offending OS and are still having trouble run this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and post the results file that ends up on your desktop.  You can run this from the LiveCD if needed.

---

### Post by john newbuntu on 2010-01-22
I do apologize Apocolyptus for misguiding you slightly.  I was assuming yours to be a WUBI install.  Please follow what ranch hand and comput3r_n3rd suggested and that will help you.

---

### Post by lordskid on 2010-01-22
> **ApocoLypTus said:**
> I was following step 15 perfectly untill i got up to the 
 
**insmod /boot/grub/_linux.mod **but when i did the command it said 
 
error: file not found
sh:grub>
 
i dont know what to do now.

There should be no underscore("_") before the linux.mod

okay it should be ```
insmod /boot/grub/linux.mod
```

No insults meant so I am deleting the line that was here although it was a fair warning without targeting anyone...


try this though if you still get the sh:grub> prompt.
```

insmod ls
ls

```
this line will show you all the drives and partitions of your computer in the form of (hd0,1) (hd0,2)... (hd0,X)

then try 
ls (hd0,1)/boot/grub
up to
ls (hd0,X)/boot/grub

well until you stop getting the file not found. take note of the number after (hd0,?)
assuming that when you ls (hd0,4) you get a list of files.
type the commands below:
```

insmod linux
insmod ext2
linux /vmlinuz root=/dev/sda4 ro
initrd /initrd.img
boot

```

---

### Post by ApocoLypTus on 2010-01-24
Thank you for ALL your help. I have tried lord's guide. well what he said to do. i typed in boot and it is doing all the stuff. As for the Grub disk image help, if this doesn't work i will use it.
 
e/ Boot Command works, But when it goes through its process, it stops at "(intiramfs)"
Is there supposed to be a command that i put in or will it leave over time? 
 
I am looking at [http://ubuntuforums.org/showpost.php?p=4450651&postcount=20](http://ubuntuforums.org/showpost.php?p=4450651&postcount=20) is that a good fix?
 
 
e/ I am going to try the disk iso stuff, i have downloaded the tar.gz file. Now all i have to do is put that on a disk, i have the disk, but i do not know how to put it on there. C0mput3r_N3rd said to just do it like you did with your Ubuntu Iso. I do not have the programs. Could i do it on a windows 7 computer? With a built in Iso program?
 
e/ Just did it with a windows 7 computer. It did not work, I put it into the dvd drive, it still came up with the grub error: [ Minmimal bash like line editing blah blah blah.. ] i am going to try to get past the intiramfs part and maybe it will work with the disc.. Nope. Didn't work. still with the (initramfs) error prompt. 
 
Don't know what to do. Maybe i didn't burn the disc right.
 
:(

---

### Post by ranch hand on 2010-01-24
Is this a wubi install?

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Is this a wubi install?
 
I do not think this is from a Wubi install. I installed it through the disk. The iso disk. I tried it out a bit from the trial, then i installed it. The installation went perfectly. like a week later, I accidently pushed the hibernate mode . I then restarted my computer and then i came up with the error: [ minimal bash-like line editing blah blah blah ] 
 
I am past that error but i have a new one. (initramfs)

---

### Post by ranch hand on 2010-01-24
I think we better have a look at the results from;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and then we will have an idea what we are dealing with.  You can run this from the LiveCD.   Where ever you run it from it will end up on your desktop.  A very nifty tool.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> I think we better have a look at the results from;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and then we will have an idea what we are dealing with.  You can run this from the LiveCD.   Where ever you run it from it will end up on your desktop.  A very nifty tool.

will do. so insert LiveCD>Trail> download the boot info script.> Run it> Then post it on here?

---

### Post by ranch hand on 2010-01-24
Yes, you will have to do that from the LiveCD too unless you transfer it to some other place.  We just want the "RESULTS.txt" from the desktop.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Yes, you will have to do that from the LiveCD too unless you transfer it to some other place.  We just want the "RESULTS.txt" from the desktop.

im on the live cd right now and dling the results.

I have the program but i dont know how to use it. Do you have to go into the terminal and type 'sudo bash ~/Desktop/boot_info_script*.sh' ?

---

### Post by ApocoLypTus on 2010-01-24
> **ApocoLypTus said:**
> im on the live cd right now and dling the results.

I have the program but i dont know how to use it. Do you have to go into the terminal and type 'sudo bash ~/Desktop/boot_info_script*.sh' ?

I dont see any RESULTS.txt file on my desktop. I have been looking around. Do i have to do something to make it come up?

---

### Post by ranch hand on 2010-01-24
Check the Downloads directory.  They added that to 9.10 and it is the default download file now.

Sorry, I forgot that.  I change the default to the Desktop as I like to see the buggers.  I ususlly put them in the Download file later.

---

### Post by ApocoLypTus on 2010-01-24
AWW BALLS! Kubuntu Froze on me. My LiveCD tends to do that. :\  I have to dl it again, 1 sec.,

e/ back on. I got the stuff :)

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   673,783,598   673,783,536   7 HPFS/NTFS
/dev/sda2         950,972,400   976,767,119    25,794,720   7 HPFS/NTFS
/dev/sda3         673,798,230   950,967,674   277,169,445   5 Extended
/dev/sda5         673,798,293   950,967,674   277,169,382  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="F462C64362C60A76" LABEL="Vista" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sda5: UUID="4d166c85-73d3-4287-bd32-3b825fc8a3f4" TYPE="ext3" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 344.9GB: boot/grub/core.img
 344.9GB: boot/grub/grub.cfg
 344.9GB: boot/initrd.img-2.6.31-14-generic
 344.9GB: boot/vmlinuz-2.6.31-14-generic
 344.9GB: initrd.img
 344.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by ApocoLypTus on 2010-01-24
Yo where is the halp O.o I need to get a file off of Vista.

---

### Post by drs305 on 2010-01-24
> **ApocoLypTus said:**
> Yo where is the halp O.o I need to get a file off of Vista.

There is no 10_linux or 30_os-prober section reported in grub.cfg. Either the /etc/grub.d/10_linux and 30_os-prober files are missing or they have been made un-executable and are not being run by update-grub.

You can mount your system partition via LiveCd and search /mountpoint/etc/grub.d to see if the files are there and if they are executable. If they are missing, you should probably check to make sure the linux and initrd files are in /boot as well.

You could also retry booting from the guide you tried earlier. There was a typo in Section 15 which has been corrected (regarding the linux.mod).  The official community doc also covers booting from the command line:  [https://help.ubuntu.com/community/Grub2#Command Line Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")

---

### Post by ranch hand on 2010-01-24
I have been busy packing wood in to the Dreaded Mother in Laws house and getting a fire going.  Then the same here.  four stoves all together.  Not real cold but the wind is blasting, we are in the middle of a "winter storm warning".  Fun times.

First off you can probably get what you need from Win JerryLewis Pro off the LiveCD.  If you have the install disk for MS you can restore its boot loader to the MBR too (I can't help there - don't allow it in the house).

Your grub.cfg output in the script is berry interesting.  No entries.

I think you better take a look at the /etc/grub.d folder from the LiveCD.  I suggest "gksudo nautilus".

There is no mention of 10_liinux (picks up your Ubuntu), 20_memtest86 (gives you your memory tests) or 30_os-prober (picks up your other OS').  You need to check that they are there.  If so you need to check that the permissions have the box checked making them executable.

Then you will need to chroot in and run;
```

update-grub

```
running "grub-install /dev/sda" wouldn't hurt.

If you have made a custom file (0x_custom) you need to make it executable and I would make 10_linux executable too.  Then run the above command.  If no custom menu ignore this.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> I have been busy packing wood in to the Dreaded Mother in Laws house and getting a fire going. Then the same here. four stoves all together. Not real cold but the wind is blasting, we are in the middle of a "winter storm warning". Fun times.
 
First off you can probably get what you need from Win JerryLewis Pro off the LiveCD. If you have the install disk for MS you can restore its boot loader to the MBR too (I can't help there - don't allow it in the house).
 
Your grub.cfg output in the script is berry interesting. No entries.
 
I think you better take a look at the /etc/grub.d folder from the LiveCD. I suggest "gksudo nautilus".
 
There is no mention of 10_liinux (picks up your Ubuntu), 20_memtest86 (gives you your memory tests) or 30_os-prober (picks up your other OS'). You need to check that they are there. If so you need to check that the permissions have the box checked making them executable.
 
Then you will need to chroot in and run;
```

update-grub

```
running "grub-install /dev/sda" wouldn't hurt.
 
If you have made a custom file (0x_custom) you need to make it executable and I would make 10_linux executable too. Then run the above command. If no custom menu ignore this.
 
I have seen the 10_Linux file. 30_os-Prober file, and the 20_memtest86 file. 
(root/etc/grub.d is where i am at)
They are .sh files. Or shell script files. 
 
I do not have my MS cd. I bought the computer with Vista on it.
 
And what is Win JerryLewis Pro?
 
And what is "gksudo nautilus".
 
And what does "grub-install /dev/sda" do? 
 
I have not made a custom file. 
 
> **drs305 said:**
> There is no 10_linux or 30_os-prober section reported in grub.cfg. Either the /etc/grub.d/10_linux and 30_os-prober files are missing or they have been made un-executable and are not being run by update-grub.
 
You can mount your system partition via LiveCd and search /mountpoint/etc/grub.d to see if the files are there and if they are executable. If they are missing, you should probably check to make sure the linux and initrd files are in /boot as well.
 
You could also retry booting from the guide you tried earlier. There was a typo in Section 15 which has been corrected (regarding the linux.mod). The official community doc also covers booting from the command line: [https://help.ubuntu.com/community/Grub2#Command Line Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")
 
The grub.d file has all the files needed i think. But they are not executables. They are .sh files. 
 
Should i change those to .exe files?
 
And the initrd and linux files are not in /boot.
 
This is confusing.
 
 
 
Should i reinstall Grub 2?

---

### Post by ranch hand on 2010-01-24
Do not change the .sh for heavens sake.

If you right click on them and choose "properties" and then the tab "permissions" you will see a box labeled "Allow executing file as a program".  That needs checked and you need to be "root" to do that which is why I recommended "gksudo nautilus".

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> And what is "gksudo nautilus".
this opens a filebrowser with root (administrator) permissions.
 
> **ApocoLypTus said:**
> And what does "grub-install /dev/sda" do?
this installs grub to the master boot record of your first drive (sda)
 
> **ApocoLypTus said:**
> The grub.d file has all the files needed i think. But they are not executables. They are .sh files.
 
Should i change those to .exe files?
like there are different kind of executables in windows (.bat, .com and the most commonly known .exe), there are different executables in *nix systems as well. .sh is comparable to the windows .bat (a script).
 
> **ApocoLypTus said:**
> And the initrd and linux files are not in /boot.
they most probably are in the root of your filesystem (/).

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Do not change the .sh for heavens sake.

If you right click on them and choose "properties" and then the tab "permissions" you will see a box labeled "Allow executing file as a program".  That needs checked and you need to be "root" to do that which is why I recommended "gksudo nautilus".

they are not Check marked with "Is executable". But i cannot click on it. I just installed Gksudo. And i ran it. I try to check the executable. Does not work.

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> they are not Check marked with "Is executable". But i cannot click on it. I just installed Gksudo. And i ran it. I try to check the executable. Does not work.
i don't know which script you are trying to run, but generally you can run a script like this:
```
sudo bash /path/to/script.sh
```if you are trying to make the grub.d scripts executable, try this:
```
sudo chmod -R +x /etc/grub.d/*
```

---

### Post by ranch hand on 2010-01-24
```

gksudo nautilus

```
This opens nautilus as root and will allow you to do this.  It will also allow you to really screw your system royally so don't do anything else and get out of it.

---

### Post by ranch hand on 2010-01-24
> **Leppie said:**
> i don't know which script you are trying to run, but generally you can run a script like this:
```
sudo bash /path/to/script.sh
```
Trying to get the 10_linux, 20_memtest86 and 30_os-prober going so that there is actually a menuentry in grub.cfg.

---

### Post by Leppie on 2010-01-24
> **ranch hand said:**
> Trying to get the 10_linux, 20_memtest86 and 30_os-prober going so that there is actually a menuentry in grub.cfg.
yeah, i later found out by re-reading some posts.
i'd suggest the command:
```
sudo chmod -R +x /etc/grub.d/*
```

---

### Post by ApocoLypTus on 2010-01-24
Okay, Now i am really confused. What am i supposed to do to fix this? I'm sorry, but i am really bad at Kubuntu as it seems.. What now?

---

### Post by ranch hand on 2010-01-24
I suggested the gui route because it is a way to see what it is that you are actually doing to the file.  I thought that was good education wise.

---

### Post by ranch hand on 2010-01-24
Run the command in leppie's post and then follow these directions ignoring the file editing as it should not be needed;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> Okay, Now i am really confused. What am i supposed to do to fix this? I'm sorry, but i am really bad at Kubuntu as it seems.. What now?
you can do either way...
just open up nautilus with root permissions, or do it the command line way.
the nautilus way is visual and might be an easier transition from windows.

---

### Post by Leppie on 2010-01-24
> **ranch hand said:**
> Run the command in leppie's post and then follow these directions ignoring the file editing as it should not be needed;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
lol.

really, go the visual way. it's more comprehensive ;)

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> you can do either way...
just open up nautilus with root permissions, or do it the command line way.
the nautilus way is visual and might be an easier transition from windows.

I did the "sudo chmod -R +x /etc/grub.d/*" Thing but it just came up with a blank screen. And when i looked to check the grub.d files, they were still non-executable.

And when i run Nautilus, It just comes up with a loading thing and no window comes up.

So i do the steps on. [https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD

---

### Post by ranch hand on 2010-01-24
Oh crap, you are on Kubuntu.  Geeze, I am a moron.  You need to get into what ever the file manager there is as root (Dolphin?).  Whatever it was that you used to look at the files with before is what you want but as "root".

Sorry, I am allergic to KDE and so blank it out.  gksudo is not right either that is for Gnome.  I am sure what it is in KDE but plane "sudo" will probably work but is a bad practice.

You will need to follow the directions on the link I gave you to run "update-grub" and "grub-install /dev/sda".  The last is probably not needed but will not hurt.

If your MS does not show up on the menu the first time you boot up to Kubuntu just pull up the terminal when you get in and run;
```

sudo update-grub

```
and that should pick it up.

If not we will work on that.

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> I did the "sudo chmod -R +x /etc/grub.d/*" Thing but it just came up with a blank screen. And when i looked to check the grub.d files, they were still non-executable.

And when i run Nautilus, It just comes up with a loading thing and no window comes up.

So i do the steps on. [https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD
could you post the output of the following command:
```
ls -al /etc/grub.d/
```

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Oh crap, you are on Kubuntu.  Geeze, I am a moron.  You need to get into what ever the file manager there is as root (Dolphin?).  Whatever it was that you used to look at the files with before is what you want but as "root".

Sorry, I am allergic to KDE and so blank it out.  gksudo is not right either that is for Gnome.  I am sure what it is in KDE but plane "sudo" will probably work but is a bad practice.

You will need to follow the directions on the link I gave you to run "update-grub" and "grub-install /dev/sda".  The last is probably not needed but will not hurt.

If your MS does not show up on the menu the first time you boot up to Kubuntu just pull up the terminal when you get in and run;
```

sudo update-grub

```
and that should pick it up.

If not we will work on that.

So just do all the steps that you said to do on the link.

I am doing all the steps . But when i put in 
sudo mount /dev/sda2 /mnt/boot or any other 
sudo mount /dev/sdaX /mnt it all just comes up blank. Is that normal?

> **Leppie said:**
> that makes 2 of us...

konquerer should be the default browser/filemanager in kde...

Actually Dolphin is Main filemanager and Konqueror is the default browser. It came with that.

---

### Post by Leppie on 2010-01-24
> **ranch hand said:**
> Oh crap, you are on Kubuntu.  Geeze, I am a moron.  You need to get into what ever the file manager there is as root (Dolphin?). 
that makes 2 of us...

konquerer should be the default browser/filemanager in kde...

---

### Post by ApocoLypTus on 2010-01-24
Done all the terminal stuff. Im rebooting now.

---

### Post by ApocoLypTus on 2010-01-24
> **ApocoLypTus said:**
> Done all the terminal stuff. Im rebooting now.
 
OMG!. Its back at the [ Minimal BASH-like line editing blah blah blah... ] 
 
Now what.., :(

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> OMG!. Its back at the [ Minimal BASH-like line editing blah blah blah... ] 
 
Now what.., :(
could you post the output of this command:
```
ls -al /etc/grub.d/
```

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> could you post the output of this command:
```
ls -al /etc/grub.d/
```
 
error: file not found
 
sh:grub>_

---

### Post by Leppie on 2010-01-24
i meant, once you're back in your system...

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> i meant, once you're back in your system...
 
OOO!!! Lmao okay. Sorry.

```
total 17
drwxr-xr-x   2 root root  143 2009-10-27 18:37 .
drwxr-xr-x 129 root root  640 2010-01-24 23:25 ..
-rwxr-xr-x   1 root root 3296 2009-10-24 00:43 00_header
-rwxr-xr-x   1 root root 1154 2009-10-24 00:31 05_debian_theme
-rwxr-xr-x   1 root root 3778 2009-10-24 00:43 10_linux
-rwxr-xr-x   1 root root  772 2009-10-23 16:24 20_memtest86+
-rwxr-xr-x   1 root root 5332 2009-10-24 00:43 30_os-prober
-rwxr-xr-x   1 root root  214 2009-10-24 00:43 40_custom
-rw-r--r--   1 root root  483 2009-10-24 00:43 README
```

---

### Post by drs305 on 2010-01-24
> **ApocoLypTus said:**
> OMG!. Its back at the [ Minimal BASH-like line editing blah blah blah... ] 
 
Now what.., :(

Try typing this at the prompt:
```

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod /boot/grub/linux.mod
insmod /boot/grub/ext2.mod
linux /vmlinuz-2.6.31-14-generic root=/dev/sda5 ro
initrd /initrd.img-2.6.31-14-generic
boot

```

If the linux and initrd lines don't work, try
```
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.31-14-generic
boot
```

---

### Post by ApocoLypTus on 2010-01-24
> **drs305 said:**
> Try typing this at the prompt:
```

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod /boot/grub/linux.mod
insmod /boot/grub/ext2.mod
linux /vmlinuz-2.6.31-14-generic root=/dev/sda5 ro
initrd /initrd.img-2.6.31-14-generic
boot

```

If the linux and initrd lines don't work, try
```
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro
initrd /boot/initrd.img-2.6.31-14-generic
boot
```

I will try that. But i have tried it before and the linux.mod and initrd did not work for me. so i guess i will try it with the other way you told me.

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> OOO!!! Lmao okay. Sorry.

```
total 17
drwxr-xr-x   2 root root  143 2009-10-27 18:37 .
drwxr-xr-x 129 root root  640 2010-01-24 23:25 ..
-rwxr-xr-x   1 root root 3296 2009-10-24 00:43 00_header
-rwxr-xr-x   1 root root 1154 2009-10-24 00:31 05_debian_theme
-rwxr-xr-x   1 root root 3778 2009-10-24 00:43 10_linux
-rwxr-xr-x   1 root root  772 2009-10-23 16:24 20_memtest86+
-rwxr-xr-x   1 root root 5332 2009-10-24 00:43 30_os-prober
-rwxr-xr-x   1 root root  214 2009-10-24 00:43 40_custom
-rw-r--r--   1 root root  483 2009-10-24 00:43 README
```
sorry, did you boot off the livecd?
then you have to change the commands:
```
sudo mount /dev/sda5 /mnt
ls -al /mnt/etc/grub.d/
```

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> sorry, did you boot off the livecd?

Yes i did. I cannot get to the grub boot menu. Should i try what drs305 said to do? Then see if i can get onto the grub boot menu?

e/ with new commands you told me to do,
```
total 40
drwxr-xr-x   2 root root 4096 2009-10-27 18:37 .
drwxr-xr-x 123 root root 4096 2010-01-21 03:58 ..
-rwxr-xr-x   1 root root 3296 2009-10-24 00:43 00_header
-rwxr-xr-x   1 root root 1154 2009-10-24 00:31 05_debian_theme
-rw-r--r--   1 root root 3778 2009-10-24 00:43 10_linux
-rw-r--r--   1 root root  772 2009-10-23 16:24 20_memtest86+
-rw-r--r--   1 root root 5332 2009-10-24 00:43 30_os-prober
-rwxr-xr-x   1 root root  214 2009-10-24 00:43 40_custom
-rw-r--r--   1 root root  483 2009-10-24 00:43 README

```

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> I will try that. But i have tried it before and the linux.mod and initrd did not work for me. so i guess i will try it with the other way you told me.
you could try the following at the grub prompt:
```
set root=(hd0,5)
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

---

### Post by drs305 on 2010-01-24
> **ApocoLypTus said:**
> I will try that. But i have tried it before and the linux.mod and initrd did not work for me. so i guess i will try it with the other way you told me.

It failed at the insmod linux step the first time due to a typo. It may work as entered above. Also, to be clear, if the kernel and initrd don't work in the first section, then do the steps in the second section. You can't run the steps only in the second part without setting the prefix and root and adding the modules.

---

### Post by ApocoLypTus on 2010-01-24
> **drs305 said:**
> It failed at the insmod linux step the first time due to a typo. It may work as entered above. Also, to be clear, if the kernel and initrd don't work in the first section, then do the steps in the second section. You can't run the steps only in the second part without setting the prefix and root and adding the modules.

Okay so i will restart computer. Go into the error prompt and type what you told me to do. Hopefully it works.

---

### Post by ApocoLypTus on 2010-01-24
When i insmod linux and ext2. They both do not work. it says unknown filesystem.
 
And when i try to the rest it says unkown filestystem.

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> When i insmod linux and ext2. They both do not work. it says unknown filesystem.
 
And when i try to the rest it says unkown filestystem.
use as first command:
```
set root=(hd0,5)
```

---

### Post by Sylslay on 2010-01-24
Grub2 is the reason, why I steel use 9.04 

Cheers 
Is not even grub2, only grub1.97 bet4 , something.

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> use as first command:
```
set root=(hd0,5)
```
 
Did that . Still does not work.
 
:\

---

### Post by ApocoLypTus on 2010-01-24
> **ApocoLypTus said:**
> Did that . Still does not work.
 
:\
 
Yeahhh It works. :D After 2 DAYS!.
 
Im on my install on Kubuntu 9.10. 
 
What now? How do i fix the rescue?

---

### Post by Leppie on 2010-01-24
> **ApocoLypTus said:**
> Yeahhh It works. :D After 2 DAYS!.
 
Im on my install on Kubuntu 9.10. 
 
What now? How do i fix the rescue?
now issue these commands:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

then before rebooting, post your grub.cfg:
```
cat /boot/grub/grub.cfg
```

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> now issue these commands:
```
sudo grub-install --recheck /dev/sda
sudo update-grub
```

then before rebooting, post your grub.cfg:
```
cat /boot/grub/grub.cfg
```

```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Theres my Grub.cfg

---

### Post by Leppie on 2010-01-24
could you also post your fstab:
```
cat /etc/fstab
```

---

### Post by ApocoLypTus on 2010-01-24
> **Leppie said:**
> could you also post your fstab:
```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 /               ext3    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ranch hand on 2010-01-24
Was this a clean install or did your upgrade from 9.04?

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Was this a clean install or did your upgrade from 9.04?

Clean install. From Disk. First time with Ubuntu,or Kubuntu.

is it safe to restart or no?

---

### Post by ranch hand on 2010-01-24
No it is not.  You do not have a menu.  This is not right.

What I would do is get rid of grub and then install grub.  This will give you a fresh start.  To do this pull up Konsole again and;
```

sudo apt-get remove grub-pc grub-common

```
That should not take long and then;
```

sudo apt-get install grub-pc grub-common

```
and then send us the grub.cfg file again.
Do not shut down or reboot.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> No it is not.  You do not have a menu.  This is not right.

What I would do is get rid of grub and then install grub.  This will give you a fresh start.  To do this pull up Konsole again and;
```

sudo apt-get remove grub-pc grub-common

```
That should not take long and then;
```

sudo apt-get install grub-pc grub-common

```
and then send us the grub.cfg file again.
Do not shut down or reboot.

I dont think that it worked.
I got this on both
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by ranch hand on 2010-01-24
Well, you could try it through your regular package manager but I have never been real impressed with Kubuntu package management.

That message usually means that some other pack manager is working.  One thing you could do is to check and see if your update manager (don't know what it is in Kubuntu) is wanting to run updates.  This is very likely if this is the first time you have been in it.  Run the updates and see if the two grub files I mentioned are updated and, if so, check your grub.cfg file and see if it has changed.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Well, you could try it through your regular package manager but I have never been real impressed with Kubuntu package management.

That message usually means that some other pack manager is working.  One thing you could do is to check and see if your update manager (don't know what it is in Kubuntu) is wanting to run updates.  This is very likely if this is the first time you have been in it.  Run the updates and see if the two grub files I mentioned are updated and, if so, check your grub.cfg file and see if it has changed.

OOOO!!! I have updates running. Right now, 48 min till done. Ill just wait for those. And anyways i got to go eat right now. After ill delete Grub. Then you tell me what to do after. Thank you for all the help you have done for me :) I really appreciate it.

---

### Post by ranch hand on 2010-01-24
Do not remove the grub files before checking the grub.cfg file.  The updates could have fixed it.

Use the;
```

cat /boot/grub/grub.cfg

```
that you used before to check it.

There could be a message when the updates end to restart the computer.  Do not do it.  It is not urgent.  We need to get you something to reboot with first.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> Do not remove the grub files before checking the grub.cfg file.  The updates could have fixed it.

Use the;
```

cat /boot/grub/grub.cfg

```
that you used before to check it.

There could be a message when the updates end to restart the computer.  Do not do it.  It is not urgent.  We need to get you something to reboot with first.

here is my Boot/grub/grub.cfg file.
```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

Not good? Or good?

---

### Post by ranch hand on 2010-01-24
OK, same crap, or seeing how you are on Kubuntu, krap.
```

sudo apt-get remove grub-pc grub-common

```and then;
```

sudo apt-get install grub-pc grub-common

```That should auto run update grub.  If you do not see it do that then;
```

sudo update-grub

```and;
```

sudo grub-install /dev/sda

```

And resend grub.cfg.

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> OK, same crap, or seeing how you are on Kubuntu, krap.
```

sudo apt-get remove grub-pc grub-common

```and then;
```

sudo apt-get install grub-pc grub-common

```That should auto run update grub.  If you do not see it do that then;
```

sudo update-grub

```and;
```

sudo grub-install /dev/sda

```

And resend grub.cfg.

Resend as in.. Post cfg?

```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by ranch hand on 2010-01-24
This is unbelievable.

Did you see it run "update-grub"?

---

### Post by ApocoLypTus on 2010-01-24
> **ranch hand said:**
> This is unbelievable.

Did you see it run "update-grub"?

I did. Ill do it again. Here ya go.

```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by Jackzor on 2010-01-24
> **ApocoLypTus said:**
> I did. Ill do it again. Here ya go.

```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

Copy and paste the terminal output for those commands that you use to remove and then reinstall grub.

So we can see exactly what you are doing and whats going on with the terminal. To make sure everything is going right from right there.

---

### Post by ApocoLypTus on 2010-01-24
> **Jackzor said:**
> Copy and paste the terminal output for those commands that you use to remove and then reinstall grub.

So we can see exactly what you are doing and whats going on with the terminal. To make sure everything is going right from right there.

Okay.

```
xander@xander-desktop:~$ sudo apt-get remove grub-pc grub-common
Reading package lists... Done                                   
Building dependency tree                                        
Reading state information... Done                               
The following packages will be REMOVED:                         
  grub-common grub-pc                                           
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.  
After this operation, 4,235kB disk space will be freed.         
Do you want to continue [Y/n]? y                                
(Reading database ... 114138 files and directories currently installed.)
Removing grub-pc ...                                                    
Removing grub-common ...                                                
Processing triggers for man-db ...                                      
Processing triggers for ureadahead ...                                  
Processing triggers for install-info ...                                
xander@xander-desktop:~$ sudo apt-get install grub-pc grub-common       
Reading package lists... Done                                           
Building dependency tree                                                
Reading state information... Done                                       
Suggested packages:                                                     
  multiboot-doc grub-emu desktop-base                                   
The following NEW packages will be installed:                           
  grub-common grub-pc                                                   
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.          
Need to get 0B/1,453kB of archives.                                     
After this operation, 4,235kB of additional disk space will be used.    
Preconfiguring packages ...                                             
Selecting previously deselected package grub-common.
(Reading database ... 113923 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_amd64.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
Generating grub.cfg ...
done

xander@xander-desktop:~$ sudo update-grub
Generating grub.cfg ...
done
xander@xander-desktop:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
xander@xander-desktop:~$ update-grub
/usr/sbin/grub-mkconfig: You must run this as root
xander@xander-desktop:~$ sudo update-grub
Generating grub.cfg ...
done
xander@xander-desktop:~$
xander@xander-desktop:~$ sudo dpkg --configure -a
xander@xander-desktop:~$

```

That is my whole terminal on what i did. I have to go now. Will you be around tomorrow. At around 7:00 Mountain Time? 

Thank you for all the help! I really appreciate it.

---

### Post by ranch hand on 2010-01-24
That is a good idea Jackzor.

After you post those run;
```

sudo dpkg --configure -a

```
and post those results too.

---

### Post by Jackzor on 2010-01-24
Okay so.. What file is supposed to generate the files:
00_header
05_debian_theme
10_linux
30_os-probe

And so on?

I ask because I am still a noobie at this and in the process of learning.

So it may be completely obvious.. But I don't know.

---

### Post by ranch hand on 2010-01-24
There are 3 files not mentioned in the grub.cfg file which is generated by all of them.  The ones missing are 10_linux (picks up your install), 20_memtest86 (gives you the memory test) an 30_os-prober (which picks up the other OS' on your system).

If you go and look at them and check the permissions you will find that they are all marked to be executable.  The ones in question (I think) are.  Why they are not working is another question.  Replacing them from the repo on the assumtion of corruption should have fixed this.

If the current stuff does not help we will try another trick.

---

### Post by ranch hand on 2010-01-24
OK, I am, right now, on my "daytime" production OS 10.04-testing.  I run boink (World community Grid) 24/7.  I do not like to have it on an alpha release at night when I can't look in on it.

So I have to shut down and check a couple other testing OS' and then I will be back on my night  time OS 9.04.

---

### Post by Jackzor on 2010-01-24
What is the grub2 in synaptic? what exactly is a dummy package? Would reinstalling that change anything?

---

### Post by ranch hand on 2010-01-24
That is a thought, but that is the meta package and what we need is grub-pc and grub-common.

For that matter you can remove grub2 from your box if you want.  I believe it even says that in the discription.

---

### Post by ApocoLypTus on 2010-01-24
So there is no fix for now? Or what can i do to fix it? Should  i just leave it alone? But the problemo is.. That we have been having power outages.. And im afraid that it will shut down my computer. Are we going to Reinstall Grub? Or do i have to do some more commands in the terminal?
I have to go to sleep now. School tomorrow. I will be back at 7:00 PM MT. 
I hope that it will be done by tomorrow and all will be fixed. 

Thanks for all of your help. And for all you have done for me. :)

---

### Post by Jackzor on 2010-01-24
I think that if we had some screenshots of your files in the grub.d folder that show us that they are executable and showing us that they are there we maybe be able to help more.

Also. What if he just installed grub legacy in synaptic. We could try that right?

---

### Post by ranch hand on 2010-01-24
I think that the thing t odo is use the file that is working.  That would be 40-custom.  I have a Kubuntu entry ready to plug in and I have to find a MS entry.  That will not fix the problme but it will give you a working menu assuming that the problem is in those 3 files.

---

### Post by ranch hand on 2010-01-24
EDIT;
Please go to the post below and try that first.  If it does not work try this.  I have confidence that this will work but meierfra.'s solution is better.  I know it is stuff you tried before but that was when we were either not thinking about you being on the LiveCD or giving you commands that were for Ubuntu instead of Kubuntu.

OK, when ever you have the chance here are the steps.
run;
```

kdesudo kwrite /etc/grub.d/40_custom

```to make sure that we have a clean file to go to if we screw up the first thing to do is "save as" "40_custom.a".  That will be a nice clean copy of the file.

Next copy/paste this;
```

echo "Adding PhatDebian on sda7" >&2 
cat << EOF
menuentry "PhatDebian on sda7" {
        set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 so quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Vista on sda1" >&2
menuentry "Vista on sda1" {
insmod chain
insmod ntfs
search --fs-uuid --set F462C64362C60A76
chainloader +1
} 

```"save as" "40_custom" (the original file).

Go to your file manager and check the permissions of 40_custom to make sure it is still executable.

Assuming it is run;
```

sudo update-grub

```Check the grub.cfg file to see if those 2 entries are between the 
> 
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
and the
> 
### END /etc/grub.d/40_custom ###
I do not know for sure that the MS entry will work, as I said, I will not have it in the house.

I do know that the Kubuntu entry should work and never need updating either.

If it is there in the grub.cfg file run
```

sudo gurb-install /dev/sda

```reboot.

If that works reboot again and see if you can get into Win JerryLewis Pro (or whatever it is called).

If that works reboot to Kubuntu and let us know.

If not I am sure you will let us know.

Now it is time for me to hit the hay too.

EDIT
I was told the way to get to be root in a graphic app under KDE (by another Ubuntu user) is kdesu.  I ran a search on that and it seems that this is true so I edited the first command to reflect this.  I had it as "sudo kwrite".

---

### Post by meierfra. on 2010-01-25
Instead of editing the  40_custom file, you should just make the files in grub.d executable. Boot into Ubuntu (NOT the  LiveCD) and

```
sudo chmod +x /etc/grub.d/*_*
```

(You tried this before, but you were booting from the LiveCD, and that commands changed the files on the LiveCD, rather than the ones on the Ubuntu partition.)

Then run 

```
sudo update-grub
```
and update-grub should detect all your partitions.


If for some reason this does not work, do

```
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc 
```

(note that I used "purge" instead of "remove".  Configuration files (like the ones in "/etc/grub.d") are kept intact if you use "remove". But "purge" deletes them)

---

### Post by ranch hand on 2010-01-25
The OP will not be on again for about 7 hours yet.

Thanks for your input.  This sounds good to me.  I think, except for the "purge" (I think I am getting senile), that we have tried all this booted in but not all together.

We can always fall back on the custom file if this doesn't work.  Getting those files to respond correctly would definitely be, by far, the best way to go forward.  I hope it works.

Thanks again.  I am pulling my hair out.

---

### Post by meierfra. on 2010-01-25
> except for the "purge" that we have tried all this booted in 

You essentially had three attempts   to fix  the executable bit. But

```
sudo chmod +x /etc/grub.d/*
```

was only run from the LiveCD, where it should have been

```

sudo mount /dev/sda5 /mnt
sudo chmod +x /mnt/etc/grub.d/*
```


```
gksudo nautilus
```

should have been

```
kdesudo dolphin
```

and 

```
sudo apt-get remove grub-common grub-pc

```
should have been 
```
sudo apt-get purge grub-common grub-pc

```

So I'm pretty sure that the executable bits still are not set. Running


```
sudo chmod +x /etc/grub.d/*_*
```

from Ubuntu really should be all it takes to fix the problem (I'm using "*_*" instead of "*" since I don't want to make the "ReadMe" file executable, but that does not really matter)

---

### Post by ranch hand on 2010-01-25
```

sudo chmod +x /etc/grub.d/*_*

```This is a new one to me, handy to know.

I am not a KDE user at all.  It just bugs me, not even sure why.  I really like Gnome and Lxde, Xfce is all right.  I think I am just not KDE compatible.

I am happy to know the kdesudo though, never know when you may need it.

Thanks again.

EDIT

I am also very glad to have a Kubuntu user join the fray.  I was afraid they all died.

---

### Post by Leppie on 2010-01-25
> **meierfra. said:**
> ```
sudo chmod +x /etc/grub.d/*
```was only run from the LiveCD, where it should have been

```

sudo mount /dev/sda5 /mnt
sudo chmod +x /mnt/etc/grub.d/*
```
yeah, i realised only afterwards he was booting off the cd.

> **meierfra. said:**
> ```
gksudo nautilus
```should have been

```
kdesudo dolphin
```
maybe i should have a look at kde... i'm stuck with the old stuff (v.3.something)...

> **meierfra. said:**
> ```
sudo apt-get remove grub-common grub-pc

```should have been 
```
sudo apt-get purge grub-common grub-pc

```
i usually suggest to purge, just as a precaution.

> **meierfra. said:**
> ```
sudo chmod +x /etc/grub.d/*_*
```from Ubuntu really should be all it takes to fix the problem (I'm using "*_*" instead of "*" since I don't want to make the "ReadMe" file executable, but that does not really matter)
i thought of that, but i wouldn't think people would try to run a readme

---

### Post by ApocoLypTus on 2010-01-25
> **meierfra. said:**
> Instead of editing the  40_custom file, you should just make the files in grub.d executable. Boot into Ubuntu (NOT the  LiveCD) and

```
sudo chmod +x /etc/grub.d/*_*
```

(You tried this before, but you were booting from the LiveCD, and that commands changed the files on the LiveCD, rather than the ones on the Ubuntu partition.)

Then run 

```
sudo update-grub
```
and update-grub should detect all your partitions.


If for some reason this does not work, do

```
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc 
```

(note that I used "purge" instead of "remove".  Configuration files (like the ones in "/etc/grub.d") are kept intact if you use "remove". But "purge" deletes them)

I have done this but i haven't done the purge part. I think it did it right. Here is what i put in on terminal.

```
xander@xander-desktop:~$ sudo chmod +x /etc/grub.d/*_*
[sudo] password for xander:
xander@xander-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
xander@xander-desktop:~$

```

Here is my Grub.cfg file. Maybe it has changed.

```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}  
  save_env saved_entry             
  prev_saved_entry=                
  save_env prev_saved_entry        
fi                                 
insmod ext2                        
set root=(hd0,5)                   
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then                         
  set gfxmode=640x480                                                  
  insmod gfxterm                                                       
  insmod vbe                                                           
  if terminal_output gfxterm ; then true ; else                        
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output                                         
    terminal gfxterm                                                     
  fi                                                                     
fi                                                                       
if [ ${recordfail} = 1 ]; then                                           
  set timeout=-1                                                         
else                                                                     
  set timeout=10                                                         
fi                                                                       
### END /etc/grub.d/00_header ###                                        

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black        
set menu_color_highlight=black/white     
### END /etc/grub.d/05_debian_theme ###  

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1                         
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1                                            
        insmod ext2                                            
        set root=(hd0,5)                                       
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro   quiet splash                                                
        initrd  /boot/initrd.img-2.6.31-17-generic                              
}                                                                               
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {                   
        recordfail=1                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                 
        insmod ext2                                                             
        set root=(hd0,5)                                                        
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4 
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro single                                                        
        initrd  /boot/initrd.img-2.6.31-17-generic                              
}                                                                               
menuentry "Ubuntu, Linux 2.6.31-14-generic" {                                   
        recordfail=1                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                 
        set quiet=1                                                             
        insmod ext2                                                             
        set root=(hd0,5)                                                        
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4 
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro   quiet splash                                                
        initrd  /boot/initrd.img-2.6.31-14-generic                              
}                                                                               
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {                   
        recordfail=1                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                 
        insmod ext2                                                             
        set root=(hd0,5)                                                        
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4 
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro single
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set f462c64362c60a76
        chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
        insmod ntfs
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 949ca48c9ca46a86
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

If there is more that i have to do please tell me.

---

### Post by Leppie on 2010-01-25
> **ApocoLypTus said:**
> I have done this but i haven't done the purge part. I think it did it right. Here is what i put in on terminal.

```
xander@xander-desktop:~$ sudo chmod +x /etc/grub.d/*_*
[sudo] password for xander:
xander@xander-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
xander@xander-desktop:~$

```Here is my Grub.cfg file. Maybe it has changed.

```
#                                               
# DO NOT EDIT THIS FILE                         
#                                               
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub                    
#                                                                         

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then 
  have_grubenv=true                
  load_env                         
fi                                 
set default="0"                    
if [ ${prev_saved_entry} ]; then   
  saved_entry=${prev_saved_entry}  
  save_env saved_entry             
  prev_saved_entry=                
  save_env prev_saved_entry        
fi                                 
insmod ext2                        
set root=(hd0,5)                   
search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
if loadfont /usr/share/grub/unicode.pf2 ; then                         
  set gfxmode=640x480                                                  
  insmod gfxterm                                                       
  insmod vbe                                                           
  if terminal_output gfxterm ; then true ; else                        
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output                                         
    terminal gfxterm                                                     
  fi                                                                     
fi                                                                       
if [ ${recordfail} = 1 ]; then                                           
  set timeout=-1                                                         
else                                                                     
  set timeout=10                                                         
fi                                                                       
### END /etc/grub.d/00_header ###                                        

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black        
set menu_color_highlight=black/white     
### END /etc/grub.d/05_debian_theme ###  

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1                         
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1                                            
        insmod ext2                                            
        set root=(hd0,5)                                       
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro   quiet splash                                                
        initrd  /boot/initrd.img-2.6.31-17-generic                              
}                                                                               
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {                   
        recordfail=1                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                 
        insmod ext2                                                             
        set root=(hd0,5)                                                        
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4 
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro single                                                        
        initrd  /boot/initrd.img-2.6.31-17-generic                              
}                                                                               
menuentry "Ubuntu, Linux 2.6.31-14-generic" {                                   
        recordfail=1                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                 
        set quiet=1                                                             
        insmod ext2                                                             
        set root=(hd0,5)                                                        
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4 
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro   quiet splash                                                
        initrd  /boot/initrd.img-2.6.31-14-generic                              
}                                                                               
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {                   
        recordfail=1                                                            
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi                 
        insmod ext2                                                             
        set root=(hd0,5)                                                        
        search --no-floppy --fs-uuid --set 4d166c85-73d3-4287-bd32-3b825fc8a3f4 
        linux   /boot/vmlinuz-2.6.31-14-generic root=UUID=4d166c85-73d3-4287-bd32-3b825fc8a3f4 ro single
        initrd  /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set f462c64362c60a76
        chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
        insmod ntfs
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 949ca48c9ca46a86
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```If there is more that i have to do please tell me.

your grub.cfg is looking good, you should try to reboot now ;)

---

### Post by ranch hand on 2010-01-25
There, you see what happens if you do things with the right commands.

You should be able to reboot now and boot to windbloze too.

You did a fine job.  Wish I could say the same for me.

---

### Post by Leppie on 2010-01-25
> **ranch hand said:**
> There, you see what happens if you do things with the right commands.

You should be able to reboot now and boot to windbloze too.

You did a fine job.  Wish I could say the same for me.
you did a fine job as well, we all make mistakes. several heads think better than 1 ;)

---

### Post by ApocoLypTus on 2010-01-25
> **Leppie said:**
> you did a fine job as well, we all make mistakes. several heads think better than 1 ;)

So its safe to reboot? :D :D :D :D :D :D Okay! So. Ill do it now. 

Wish me Luck :D

---

### Post by Leppie on 2010-01-25
> **ApocoLypTus said:**
> So its safe to reboot? :D :D :D :D :D :D Okay! So. Ill do it now. 

Wish me Luck :D
good luck ;)

---

### Post by ApocoLypTus on 2010-01-25
> **Leppie said:**
> good luck ;)

YES! It works. But the only problem is... That i have 2 Ubuntu, 2 Windows Vista. But i think the second one of Windows Vista is my RECOVERY Drive. /sda2/ So nvm. I have 2 Ubuntus tho. And i was wondering if i could make it look a bit better. Without messing it up like last time... Cuz the original is pretty ugly.

---

### Post by Leppie on 2010-01-25
> **ApocoLypTus said:**
> YES! It works. But the only problem is... That i have 2 Ubuntu, 2 Windows Vista. But i think the second one of Windows Vista is my RECOVERY Drive. /sda2/ So nvm. I have 2 Ubuntus tho. And i was wondering if i could make it look a bit better. Without messing it up like last time... Cuz the original is pretty ugly.
you have 2 ubuntu entries as 1 is the most recent stable kernel (17) and the other one is the default stock kernel (14). i would recommend to keep both for the time being. if you have played around a bit with ubuntu and are sure the 17 kernel is working properly you can always delete the stock kernel from synaptic. but for the moment, leave it there as it could be very useful in case you have issues with the 17 kernel.

if you check the grub2 title tweaks thread in the forum, you will find the solution to omit the recovery partition in the menu. [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by ApocoLypTus on 2010-01-25
> **Leppie said:**
> you have 2 ubuntu entries as 1 is the most recent stable kernel (17) and the other one is the default stock kernel (14). i would recommend to keep both for the time being. if you have played around a bit with ubuntu and are sure the 17 kernel is working properly you can always delete the stock kernel from synaptic. but for the moment, leave it there as it could be very useful in case you have issues with the 17 kernel.

if you check the grub2 title tweaks thread in the forum, you will find the solution to omit the recovery partition in the menu. [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Well i was wondering if i could change the theme of the Grub2 bootloader, And that guide covers the rest.. But i dont understand with the Kernal (17) and (14) stuff. So i should just keep both of the Kubuntus on the bootloader?

---

### Post by Leppie on 2010-01-25
> **ApocoLypTus said:**
> Well i was wondering if i could change the theme of the Grub2 bootloader, And that guide covers the rest.. But i dont understand with the Kernal (17) and (14) stuff. So i should just keep both of the Kubuntus on the bootloader?
i would strongly recommend you to keep it as is until you understand a bit more of the system. see it as having a spare wheel in the trunk ;)

for grub2 theming, you can install the splash images:
```
sudo apt-get install grub2-splashimages
```

---

### Post by ApocoLypTus on 2010-01-25
> **Leppie said:**
> i would strongly recommend you to keep it as is until you understand a bit more of the system. see it as having a spare wheel in the trunk ;)

for grub2 theming, you can install the splash images:
```
sudo apt-get install grub2-splashimages
```

Okay thanks

---

### Post by Leppie on 2010-01-25
> **ApocoLypTus said:**
> Okay thanks
you're welcome, enjoy grub2 ;)

---

