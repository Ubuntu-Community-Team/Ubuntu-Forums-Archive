---
title: "Messed Up Grub2 after reinstalling Win 7"
date: 2009-12-19
forum: General Help
---

### Post by MaRKiV1982 on 2009-12-19
A bit of a background, i hv been dual booting Win Xp and Ubuntu 9.04, then upgraded to Karmic. Later did a upgrade to Win 7. All the while I was able to dual and triple boot without any issues.

Recently, I had a bit of a problem with windows 7 and to reinstall it, after that as expected Grub2 was lost and I recovered Karmic via live cd as in 

> [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

But now i get 2 entries for Win 7 entry

> ubuntu@ubuntu:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb1:Ubuntu karmic (development branch) (9.10):Ubuntu:linux
/dev/sdb4:Windows 7 (loader):Windows1:chain 

the second entry for Win 7 is wrong. I have only one Win 7 in sda1 and karmic in sdb1.

Here is my Fdisk output.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a634a62

Device Boot Start End Blocks Id System
/dev/sda1 * 1 3916 31455238+ 7 HPFS/NTFS
/dev/sda2 3917 60800 456920730 f W95 Ext'd (LBA)
/dev/sda3 60801 60801 7168 7 HPFS/NTFS
/dev/sda5 3917 10443 52428096 7 HPFS/NTFS
/dev/sda6 10444 23191 102398278+ 7 HPFS/NTFS
/dev/sda7 23192 35939 102398278+ 7 HPFS/NTFS
/dev/sda8 35940 48687 102398278+ 7 HPFS/NTFS
/dev/sda9 48688 60800 97297641 7 HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7218f129

Device Boot Start End Blocks Id System
/dev/sdb1 1 1911 15350076 83 Linux
/dev/sdb2 1912 3661 14056875 83 Linux
/dev/sdb3 3662 3792 1052257+ 82 Linux swap / Solaris
/dev/sdb4 * 3793 19457 125829112+ 7 HPFS/NTFS

Disk /dev/sdc: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c250c24

Device Boot Start End Blocks Id System
/dev/sdc1 1 4870 39118243+ 7 HPFS/NTFS

How do i remove the sdb4 entry from the list?

I hv tried the following nothing helps

> $ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub 

Please help...
TIA

---

### Post by john newbuntu on 2009-12-20
If you really need to remove it, one way to do it would be to do the following 3 steps:
1. Disable OS prober in /etc/default/grub by adding the following line:
GRUB_DISABLE_OS_PROBER=true

2. copy the required "menuentry" sections from /boot/grub/grub.cfg and paste(append) it into /etc/grub.d/40_custom. Save the file.

3. Run "sudo update-grub"

Remember that if you need to use a new kernel, you may have to update the 40_custom file unless you set up an entry that points to /vmlinuz and /initrd for your linux and initrd command.

---

### Post by MaRKiV1982 on 2009-12-20
Thanks for the reply.

I dont want any complications, all i wanted to know is how to remove the * from sdb4 entry i.e., make /dev/sdb4 not bootable.

> /dev/sdb4 * 3793 19457 125829112+ 7 HPFS/NTFS
I think that will solve the problem.

Any workaround to make sdb4 non-bootable like other disks?

---

### Post by ranch hand on 2009-12-20
See my sig for a good over view of Grub2.  40_custom is not a complication.  It can give you just what you want in your menu and if you use the right menu entry type your Ubuntu(s) will never need updated ever.

The second link in my post is the best in depth info on grub2 you can get.  There is a good post in Ubuntu Community Docs but it is written by the same feller (drs305) and the link I give is to the How To section of these forums and his sig has links to his other How to's that are equally great.

---

### Post by MaRKiV1982 on 2009-12-20
Thanks Ranch, i would go thru ur entry. But i wanted to know why sdb4 is taken as bootable when no OS is present in there... is there a way to solve that mystery?

---

### Post by james2b on 2009-12-20
You can boot to a partition tool such as the Linux based GParted and is here; [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) ,then just go to get the iso file downloaded, and burn to a CD-RW. Then when you boot to it, change the active boot flag partition from sdb4 to the sdb1, and reboot. The GParted partition tool is also on this CD; [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by ranch hand on 2009-12-20
> **MaRKiV1982 said:**
> Thanks Ranch, i would go thru ur entry. But i wanted to know why sdb4 is taken as bootable when no OS is present in there... is there a way to solve that mystery?
The best way to look at boot problems is with this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

run that and take a look at the results file and post it here.

Running 10.04testing you have a more advanced gparted on your LiveCD than you will get anywhere else.

Gparted Live doesn't even want you to use the newest version of their CD as it is buggy.

---

### Post by Leppie on 2009-12-20
> **MaRKiV1982 said:**
> Thanks for the reply.

I dont want any complications, all i wanted to know is how to remove the * from sdb4 entry i.e., make /dev/sdb4 not bootable.


I think that will solve the problem.

Any workaround to make sdb4 non-bootable like other disks?

you can use fdisk, or cfdisk to change the boot flag for a partition.

---

### Post by MaRKiV1982 on 2009-12-20
Thanks Ranch, i hv attached the script output here... 

i hv used gparted to use remove the boot flag from sdb4 and changed the partition from Physical to Logical. but still sdb5 (changed from sdb4) acts as a boot partition for a non existing Win 7 OS.

The output of the script shows that sdb5 has a bootmgr in it..

> sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

---

### Post by ranch hand on 2009-12-20
Oh, this is neat.  Isn't that a great script?  I see you are into messing with your box as I am.

Sdb5 is labeled as "Dump" and is ntfs.  I do not know what is in that partition, but I can assure you that there is a piece of the MS boot system or kernel in there that os-prober is picking up.

I was afraid that it was something really screwed.

If you are pretty much happy with the way your box is set up and are not going to change OS' in the near future ( next couple of weeks) I would just do away with os-prober in the manner below.

First I would be sure to have "nautilus-gksu" installed, handy bugger.  You need to reboot to get it into your right click menu.

If thing to do would be to open /etc/grub.d/40_custom by right clicking on /etc and then on the option "open as administrator", you will need to enter your pass word.  You are now in /etc as root.

Open grub.d and then get 40_custom in your text editor (I like gedit but there are lots) and wipe every thing out and put this in;
```

#!/bin/sh
# This file is an example on how to add custom entries

echo "Adding Karmic on sdb1" >&2 
cat << EOF
menuentry "Karmic on sdb1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}
EOF

echo "Adding Daily on sda13" >&2 
cat << EOF
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 946caa3a6caa1750
    chainloader +1
}
EOF

```
Save that file as 06_custom.

That Karmic entry will work for any kernel.  If you hit "e" in the boot menu and replace the "ro quiet splash" with single, you will boot to recovery.

Open the permissions on 06_custom and make sure that the box is checked to make it executable (Allow executing file as program).

Open a terminal and run;
```

sudo update-grub

```
The read out should have to "Adding this or that" entries at the top.

At this point, I would reboot and make sure that the entries work.  I am sure they will but I wouldn't be if I were you.

After they work go back in as administrator and open the permissions of /etc/grub.d/<any/all file(s) from 10_linux up to 40_custom> that you do not want cluttering up your menu with their input and uncheck the executable box.  They are now inactive.

I am on 10.04 Alpha1 so I like to leave the 10_linux input coming.  Who uses memtest86? 

Run "update-grub" again and go to /boot/grub/grub.cfg (you need to do this on the root nautilus that you have open so you can open grub.cfg) and take a look.

Reboot that and you will like it.

While in there you could a background image (.png) in /usr/share/images/desktop-base and insert the name of that file into 05_debian-theme like this;
```

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/menu.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i

```
compare that to yours and you will see what I mean.

if you do that make the image 700x500 to start with, it will probably be OK.

You will of coarse need to run "update-grub" to get that to actually be changed.

---

### Post by Leppie on 2009-12-20
> **MaRKiV1982 said:**
> Thanks Ranch, i hv attached the script output here... 

i hv used gparted to use remove the boot flag from sdb4 and changed the partition from Physical to Logical. but still sdb5 (changed from sdb4) acts as a boot partition for a non existing Win 7 OS.

The output of the script shows that sdb5 has a bootmgr in it..

delete the files/folders (the ones present on the disk)?
```
bootmgr /Boot grldr
```

---

### Post by Leppie on 2009-12-20
Alternatively you could add the following to your 30_os_prober:
```
if [ "$LONGNAME" = "Windows 7 (loader)" ] && [ "${DEVICE}" = "/dev/sdb5" ] ; then
continue
fi
```

this will skip adding the partition to your boot menu.

---

### Post by MaRKiV1982 on 2009-12-25
Thanks a lot Leppie and Ranch, your help was awesome.. Now my rig is back to pristine condition :D

Wish u happy year ending and enjoyable holidays

---

### Post by ranch hand on 2009-12-25
The same wishes to you and yours.

Glad you are up and running with a menu you can stand.  I know that this is important to me.

---

