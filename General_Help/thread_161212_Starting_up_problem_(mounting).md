---
title: "Starting up problem (mounting)"
date: 2006-04-16
forum: General Help
---

### Post by JohanSwe on 2006-04-16
I was trying to convert a NTFS partition to FAT32 with Partition commander. But I restarted my computer after the partition only had been analysed because the program told me to run scandisk.

But then I got a problem with grub. Error 17. Problem with mounting. I then installed a new copy of ubuntu to another partition and a new partition was created as swap disc. 

And now grub can load my original copy of ubuntu. But I get this error while starting up. And the loading stops and I get a prompt.

```
Decompressing Linux...done.
Booting kernel.
Loading, please wait
FATAL: Module unknown not found.
mount: Mounting /dev/sda7 on /root failed: No such device
mount: Mounting/root/dev on /dev/.static/dev faild: No such file or directory
Target filesystem doesn't have /sbin/init
``` 
How can I fix this? Can I install a new copy of Ubuntu over my original install. Or will all my settings getting lost then? :confused:

---

### Post by z_diver on 2006-04-16
To start with, do you have a Live CD and do you know if you have a scsi, ATA or SATA drive?  If you have a Live CD you can find out what your computer sees for drives by running the commands below in a terminal:
```
[COLOR="DarkRed"]sudo lshw|grep hd[/COLOR]
```
and
```
[COLOR="DarkRed"]sudo lshw|grep sd[/COLOR]
```

Then you should make sure the partitions listed in fstab coincide with your drive or drives.  You should probably check using fdisk and comparing the output to fstab on the drive you installed ubuntu on and are trying to boot.  Depending on the output you get from the lshw commands above, run fdisk on the hard disks.  They will be something like /dev/hda, /dev/hdb or /dev/sda.  To find the partions on the drives use:
```
sudo fdisk /dev/hda
```(or substitue /dev/sda if it exists); then at the fdisk prompt press 'p' to show the list of partitions.  Press 'q' to quit fdisk.

At this point you may already be able to figure out what the problem is.  Post some of these results and we'll help you mount the correct partition and edit the fstab file so the system boots.

---

### Post by JohanSwe on 2006-04-16
Thank you very much :)

I got no live cd. Should I get one? Or can I use my installalation cd. 

I got a SATA drive

---

### Post by z_diver on 2006-04-16
[QUOTE=JohanSwe]
I got no live cd. Should I get one? Or can I use my installalation cd. 

I got a SATA drive[/QUOTE]
Well, at this stage you are unable to boot as I understand it.  You have to be able to run a few commands in order to fix most boot problems.  I would probably use a Live CD, although the Dapper Flight 5 or 6 install CDs may have a Rescue option from what I understand.  Even if you are using Dapper, I'd use the Live CD version because it can be used to install in addition to give you a full gui in which to trouble-shoot.

If you have the regular Dapper installation CD and it offers the rescue option when booting, try that.  On Suse, this option can look at your drives, see where grub resides, where the linux kernels are and rewrite /etc/fstab to allow the system to boot.

We will do the same thing but it will be a manual process.  Not too difficult but the steps are not obvious for users not familiar with grub.

---

### Post by JohanSwe on 2006-04-17
[QUOTE=z_diver]Well, at this stage you are unable to boot as I understand it.[/QUOTE]
Yes and no. I can choose to boot ubuntu from grub, but in an early stage of booting ubuntu gets mounting problems and stops. Now I'm standing at a prompt. I tried typing sudo "lshw|grep hd" but I got "command not found".
[QUOTE=z_diver]You have to be able to run a few commands in order to fix most boot problems.  I would probably use a Live CD, although the Dapper Flight 5 or 6 install CDs may have a Rescue option from what I understand. Even if you are using Dapper, I'd use the Live CD version because it can be used to install in addition to give you a full gui in which to trouble-shoot
If you have the regular Dapper installation CD and it offers the rescue option when booting, try that..[/QUOTE]
I couldn't find a rescue option at my installation cd. (It is 2 months old.)
[QUOTE=z_diver]On Suse, this option can look at your drives, see where grub resides, where the linux kernels are and rewrite /etc/fstab to allow the system to boot. 
We will do the same thing but it will be a manual process.  Not too difficult but the steps are not obvious for users not familiar with grub.[/QUOTE]
I got Suse 10 that's working and the suse installation cd.

Should I downlaod the Ubuntu live cd anyway? Also I got another copy of ubuntu at another partition that is working. Maybe I could do it from there?

---

### Post by JohanSwe on 2006-04-17
[QUOTE=z_diver]Well, at this stage you are unable to boot as I understand it.  You have to be able to run a few commands in order to fix most boot problems.  I would probably use a Live CD, although the Dapper Flight 5 or 6 install CDs may have a Rescue option from what I understand.  Even if you are using Dapper, I'd use the Live CD version because it can be used to install in addition to give you a full gui in which to trouble-shoot.

If you have the regular Dapper installation CD and it offers the rescue option when booting, try that.  On Suse, this option can look at your drives, see where grub resides, where the linux kernels are and rewrite /etc/fstab to allow the system to boot.

We will do the same thing but it will be a manual process.  Not too difficult but the steps are not obvious for users not familiar with grub.[/QUOTE]

[QUOTE=z_diver]To start with, do you have a Live CD and do you know if you have a scsi, ATA or SATA drive?  If you have a Live CD you can find out what your computer sees for drives by [COLOR="Red"]**running the commands below in a terminal**[/COLOR]:
```
[COLOR="DarkRed"]sudo lshw|grep hd[/COLOR]
```
and
```
[COLOR="DarkRed"]sudo lshw|grep sd[/COLOR]
```
[/QUOTE]
In what terminal? From a terminal in ubuntu after booting from the live cd?

---

### Post by z_diver on 2006-04-18
[QUOTE=JohanSwe]
I got Suse 10 that's working and the suse installation cd.

Should I downlaod the Ubuntu live cd anyway? Also I got another copy of ubuntu at another partition that is working. Maybe I could do it from there?[/QUOTE]
You will probably be fine booting into either Suse or the working Ubuntu installation and running the commands I listed.

The commands are merely to print out details about your installation.  We're going to need to know which partition contains which installation of Ubuntu(working and not working) and which contains the Suse 10.  Once we have that we can edit the correct menu.lst file and it should boot fine. 

It is possible that the Suse 10 rescue option can fix this also but I'd rather try to do it manually first.  We will be able to back everything up in case it doesn't work, and then you can try the rescue disk. ;)

Oh, you were correct.  You can run the commands from any working terminal.  The disks will NOT need to be mounted in order to run lshw and fdisk.  Later, when we edit /boot/grub/menu.lst, we will mount a partition.

---

### Post by JohanSwe on 2006-04-18
Thank you
```
Disk /dev/sda: 203,9 GB, 203928109056 byte
255 huvuden, 63 sektorer/spår, 24792 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531       21119   157348642+   f  W95 Utökad (LBA)
/dev/sda3           21120       24792    29503372+  83  Linux
/dev/sda5            1531       16828   122881153+   7  HPFS/NTFS
/dev/sda6           16829       19377    20474811    b  W95 FAT32
/dev/sda7           19378       19504     1020096   82  Linux växling / Solaris
/dev/sda8           19505       20450     7598713+  83  Linux
/dev/sda9           20451       20959     4088511   83  Linux
/dev/sda10          20960       21119     1285168+  82  Linux växling / Solaris
```

The fstab when running working (empty) ubuntu:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sda5 /media/sda5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 vfat rw,user,fmask=0111,dmask=0000 0 0
```

---

### Post by JohanSwe on 2006-04-18
In grub startup list it says:
Ubuntu (not working) /dev/sda9
Suse /dev/sda8


And working Ubuntu (where I am now): /dev/sda3

---

### Post by JohanSwe on 2006-04-18
I tried to mount sda9 with my broken ubuntu but I can't. This is the first time I am mounting so I don't now if this is the right way of doing it:

> Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531       21119   157348642+   f  W95 Utökad (LBA)
/dev/sda3           21120       24792    29503372+  83  Linux
/dev/sda5            1531       16828   122881153+   7  HPFS/NTFS
/dev/sda6           16829       19377    20474811    b  W95 FAT32
/dev/sda7           19378       19504     1020096   82  Linux växling / Solaris
/dev/sda8           19505       20450     7598713+  83  Linux
[color=red]/dev/sda9           20451       20959     4088511   83  Linux[/color]
/dev/sda10          20960       21119     1285168+  82  Linux växling / Solaris
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda10      none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#Added by diskmounter utility
/dev/sda5 /media/sda5 ntfs ro,user,fmask=0111,dmask=0000 0 0
#Added by diskmounter utility
/dev/sda6 /media/sda6 vfat rw,user,fmask=0111,dmask=0000 0 0

[color=red]
#added by me
/dev/sda9   /media/ubu   ext3    defaults 0       0[/color]

> johan@ubuntu:~$ sudo mount -a
mount: mountingpoint /media/ubu doesn't exist

---

### Post by JohanSwe on 2006-04-18
-Solved-

I edited:
/etc/fstab
/boot/grub/menu.lst
on both ubuntu partitions.

Thank you
:)

---

### Post by z_diver on 2006-04-18
[QUOTE=JohanSwe]-Solved-

I edited:
/etc/fstab
/boot/grub/menu.lst
on both ubuntu partitions.

Thank you
:)[/QUOTE]
Great.  Glad you figured it out.  Looks like the problem with the first mounting attempts were that the folder ubu was not yet created inside of /media.

As for GRUB, when it is setup, it's installed to the MBR but tells itself to look at XYZ partition and usually to read the file called /boot/grub/menu.lst on that partition in order to provide a list of boot options for the user.  I'm mentioning this so you can see that only one menu.lst is being used on any given system at a time.  But then it's good that you edited both fstabs becasue they are certainly both necessary(one for each installation) and if you have a 3rd, that should look somewhat similar to the others as well if you want to access all the partitions from all installations.

So what probably went wrong with the install in the first place is GRUB added entries to the wrong /boot/grub/menu.lst when the boot sector was pointing at a menu.lst on another partition.  During the install the partitions changed order a bit and made the original menu.lst inaccurate so nothing could boot.  I guess you were stuck at a simple grub prompt.

It's good you got it back and didn't loose any settings or data.  Way to go.

---

### Post by JohanSwe on 2006-04-19
Is there a way to edit grub in the MBR? I want to delete my recently installed ubuntu (and the menu.lst).

> So what probably went wrong with the install in the first place is GRUB added entries to the wrong /boot/grub/menu.lst when the boot sector was pointing at a menu.lst on another partition. During the install the partitions changed order a bit and made the original menu.lst inaccurate so nothing could boot. I guess you were stuck at a simple grub prompt.
No, after the installation I could boot everything but my old ubuntu. I could see the old ubuntu loading image for 2 sec but then got the text message I have quoted, and then a prompt (a linux prompt?).

To me it seems like the new ubuntu took the boot settings (for the old ubuntu) from the old menu.lst and imported that to the new menu.lst (in the new ubuntu). 
Could it be like that?

And I don't understand this part:
[QUOTE=z_diver]if you have a 3rd, that should look somewhat similar to the others[/QUOTE]

---

### Post by z_diver on 2006-04-19
[QUOTE=JohanSwe]Is there a way to edit grub in the MBR? I want to delete my recently installed ubuntu (and the menu.lst).[/quote]
First: although grub is installed to the mbr, editing is usually done in the menu.lst file which resides on a hd partition so there is no benefit of doing the editing from within grub unless you cannot boot.  That said, if you can not boot you can try to fix it *temporarily* by pressing 'e' to edit the entries directly from the grub prompt. *[COLOR="DarkRed"]Temporarily[/COLOR]* because you are only editing the file in memory, not the hard disk.

You can also press "c" at the grub pompt.  From there you see what grub sees for disks by typing:
```
root (hd[COLOR="DarkRed"]press TAB[/COLOR],[COLOR="DarkRed"]press TAB[/COLOR])
``` There is much more you can do with grub but it's too much to list here.  Look it up on the web.

Second: You can remove the entry from fstab but that will only make it not appear on the grub menu.  To litterally delete the entire installation you can use fdisk or gparted.  Just be VERY careful that you know exactly what partition you are working on and make backups!  IT PAYS OFF IN THE LONG RUN.
> 
To me it seems like the new ubuntu took the boot settings (for the old ubuntu) from the old menu.lst and imported that to the new menu.lst (in the new ubuntu). 
Could it be like that?If you saw an entry for the newer Ubuntu installation, that is entirely possible.  But again, if there was no entry for the new install, my bet would be that grub read the disks differently and the mbr record on hda was not updated to point to your new installation's partition and instead it loaded the old menu.lst which was no longer very accurate.  Hence you could boot some partitions but not others.

What I meant by '3rd fstab' is that if you have a Suse 10 installation on that disk, you can make entries for the ubuntu partitions and create the necessary mount points(just a fancy name for directories) so you can move data back and forth between all your disks.  That can be handy so you don't have lots of redundant data.

---

### Post by JohanSwe on 2006-04-19
> **z_diver]
To litterally delete the entire installation you can use fdisk or gparted.  Just be VERY careful that you know exactly what partition you are working on and make backups!  IT PAYS OFF IN THE LONG RUN.[/QUOTE]
Sure, it does  said:**
> 
If you saw an entry for the newer Ubuntu installation, that is entirely possible.  But again, if there was no entry for the new install, my bet would be that grub read the disks differently and the mbr record on hda was not updated to point to your new installation's partition and instead it loaded the old menu.lst which was no longer very accurate.  Hence you could boot some partitions but not others.
I saw an entry for the newer ubuntu (and all my other OS's) and I could load it. But I could not load the original ubuntu, because the pointing was after the installation (of the newer ubuntu) to the wrong partition: the same partition as the original ubuntu _before_ the installation added a partition. So the information for that pointing (added to menu.lst in the newer ubuntu) must have been taken from:

1. Some file on the original ubuntu partition.
2. From grub at the mbr record

:-k

---

### Post by Spunky Alven on 2006-04-20
Dunno if i have the same problem but it sounds like it. I Tried to help a friend to uppgrade from Hoary to Breezy using the Breezy CD. All the uppdates installed fine. I restarted and in the Grub menu i chosed Ubuntu but here commes the problem. Grub shows some text that quickly disapers and then the screen is blank and nothing happens. Grub can still load windows so it seems like grub is still working.
[Followed this guide]("http://ubuntuforums.org/showthread.php?t=24113") but at step 6 the installer complains that it can't finnd the root partition.

As i can se either Grub has become corupted in some way or the Unbunt partion has become corupted. All help are welcome.

---

### Post by JohanSwe on 2006-04-20
[QUOTE=Spunky Alven]Dunno if i have the same problem but it sounds like it. I Tried to help a friend to uppgrade from Hoary to Breezy using the Breezy CD. All the uppdates installed fine. I restarted and in the Grub menu i chosed Ubuntu but here commes the problem. Grub shows some text that quickly disapers and then the screen is blank and nothing happens. Grub can still load windows so it seems like grub is still working.
[Followed this guide]("http://ubuntuforums.org/showthread.php?t=24113") but at step 6 the installer complains that it can't finnd the root partition.

As I can see either Grub has become corupted in some way or the Unbunt partion has become corupted. All help are welcome.[/QUOTE]
I don't think you have the same problem because I didn't get the black screen and for me ubuntu started to load but then got mounting problems because of wrong linking to the partitions.

But maybe we could solve it in a quite similar way. I don't know.

But trying to follow that guide seems to be a good start. 

So the installer complains that it can't find the root partition. But can you see that partition when you have selected "Manual Partition" (step 3)? 

And have you defined which partition is "root" and which is "swap" (step 4)? (Sorry, I don't know what "boot" is:confused:  )

---

### Post by z_diver on 2006-04-20
[QUOTE=JohanSwe]But the problem is that the menu.lst grub is pointing to is on that disk. So I need to change grub and I don't know how :confused: [/quote]
OK, no big deal.  We just need to re-setup grub to point to your original Ubuntu installation.  I guess that is well located by now.:D You can run the command below from the gnome-terminal.  Note: Since grub has already been installed to the MBR, these commands, will work from the grub promp also if you press "c" at the menu.  
```

#[COLOR="DarkRed"]sudo grub[/COLOR]
grub> [COLOR="DarkRed"]find /boot/grub/stage1[/COLOR]
```
That will give you a list of partitions grub can find installations on.  Choose your original Ubuntu partition and run the command below replacing the variables as necessary.
```
grub> [COLOR="DarkRed"]root (hdx,y)[/COLOR]
 Filesystem type is ext2fs, partition type 0x83
grub> [COLOR="DarkRed"]setup (hdx)[/COLOR]
grub> [COLOR="DarkRed"]quit[/COLOR]
```
If the output shows "succeeded" you should be able to boot from your old ubuntu installation but that will also mean that you have to make sure it's menu.lst accurately represents the new partition structure.  If it's not mounted in your new install, mount it now and check that /some-mount-point/boot/grub/menu.lst has the right partition info listed.  If for some reason, you do not get it to boot properly, you can use the "e" command at the grub menu to change the partition to something functional so you can boot.

---

### Post by z_diver on 2006-04-20
[QUOTE=Spunky Alven]Grub shows some text that quickly disapers and then the screen is blank and nothing happens. Grub can still load windows so it seems like grub is still working.
[Followed this guide]("http://ubuntuforums.org/showthread.php?t=24113") but at step 6 the installer complains that it can't finnd the root partition.
[/QUOTE]
The fact that grub shows the menu and boots to Windows means grub itself is functional.  The issue is must have to do with either:

A) grubs not finding the right partition or
B) The files that grub is finding on the right partition are incorrectly identifying what to boot.

Run the commands I listed in my previous post([COLOR="DarkSlateBlue"]#18[/COLOR] in this thread) from the grub boot prompt by typing "[COLOR="Red"]c[/COLOR]" at the grub menu to enter the grub shell.  That will fix the system if it's problem A.  If for some reason that does not work, post back with some additional output from those commands and we'll get you going by editing [COLOR="DarkSlateBlue"]/boot/grub/menu.lst[/COLOR] on his ubuntu partition using a live Cd.  Similar to how it was done in the link you sent.

---

### Post by Spunky Alven on 2006-04-21
Thanks, will try all of your suggestions on omdat when i meet my friend.

---

### Post by JohanSwe on 2006-04-23
thank you z_diver!
I have deleted my newer ubuntu partition and suse, and everything works just fine :D

---

