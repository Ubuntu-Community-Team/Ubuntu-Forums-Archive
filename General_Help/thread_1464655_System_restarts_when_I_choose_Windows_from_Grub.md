---
title: "System restarts when I choose Windows from Grub"
date: 2010-04-28
forum: General Help
---

### Post by Jaygan on 2010-04-28
I recently dual booted Windows Vista and Ubuntu.  When I restart my computer I am given the option between Ubuntu and Windows.  If I choose Windows the computer restarts and returns me to this selection screen.  Ubuntu starts normally.  I just started using linux so my experience is quite limited.

Thanks for the help.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
That would be a problem with windows...

---

### Post by dino99 on 2010-04-28
> **Jaygan said:**
> I recently dual booted Windows Vista and Ubuntu.  When I restart my computer I am given the option between Ubuntu and Windows.  If I choose Windows the computer restarts and returns me to this selection screen.  Ubuntu starts normally.  I just started using linux so my experience is quite limited.

Thanks for the help.

that mean it dont find windows, edit boot line, the uuid have probably changed

---

### Post by oldfred on 2010-04-28
This will help us understand your entire system:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by antrozous812 on 2010-04-29
(removed by the author)

---

### Post by GSF1200S on 2010-04-29
My first impulse would be to run:
```
sudo update-grub2
```
from Ubuntu. That should find other operating systems and add them to grub (it did for me). Im still used to Grub 1, so Im a bit green with Grub 2.

You can give Oldfred's suggestion a thought. I would be interested to see the results of:
```
sudo fdisk -l
```
followed by the contents of the file located at:
```
/boot/grub/grub.cfg
```
Perhaps then I could help you figure out why its not loading windows (no guarantees; it seems odd that it will only boot the previous OS). Correct me if Im wrong, but it seems the OP cannot get windows to load, which would suggest that grub is looking for the wrong UUID or hd(0,*) designation? Some of the other responses seem to be a different problem..

---

### Post by antrozous812 on 2010-04-29
(removed by the author)

---

### Post by oldfred on 2010-04-29
Jaygan,
Usually windows not booting indicates some problem with windows and the boot info script will often show us if files are missing and what may be the best way to repair it.

antrozous812
Please do not hijack someone else's thread. Now your results.txt gets confused with Jaygan's. Your problem is different since it relates to booting  both. Did you try what I suggested in your thread? I just helped a user yesterday whose motherboard seemed not to allow grub to use UUID. Removed search line and changed UUIDs to sdaX style and he worked. (He figured most of it out on his own, so I cannot take credit)

---

### Post by antrozous812 on 2010-04-29
Oldfre, and Jaygan, I'm sorry for "hijacking" the thread but I sincerely thought that it would be related. I am a complete beginner at Linux, and thought it could be related. 
I'm sorry for the inconvenience.

Yes, I have tried all the suggestions in my thread, but it didn't work. I will try your suggestion and not interfere with this thread! 

I'm sorry again and I have delete my own posts.

---

### Post by Jaygan on 2010-05-03
Oldfred, I tried the boot info option and it keeps returning "No such file or directory"

GSF: sudo update-grub 2 had the following output

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done
```

sudo fdisk -l had the had the output

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18387c7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       12553    94534372+   7  HPFS/NTFS
/dev/sda3           12554       24321    94526460    5  Extended
/dev/sda5           12554       23837    90638698+  83  Linux
/dev/sda6           23838       24321     3887698+  82  Linux swap / Solaris
```

And 
/boot/grub/grub.cfg
came up with permission denied.

---

### Post by oldfred on 2010-05-03
Some versions of liveCDs download to desktop &  some newer ones download to ~/downloads. You have to check where it downloaded and run the commands from that location. I think the instructions on link site explain that.

---

### Post by Animal X on 2010-05-03
> **Jaygan said:**
> I recently dual booted Windows Vista and Ubuntu.  When I restart my computer I am given the option between Ubuntu and Windows.  If I choose Windows the computer restarts and returns me to this selection screen.  Ubuntu starts normally.  I just started using linux so my experience is quite limited.

Thanks for the help.



what does your menu.lst file look like?

---

### Post by Animal X on 2010-05-03
> **Sin@Sin-Sacrifice said:**
> That would be a problem with windows...
not necessarily, maybe grub isnt configured properly...

---

### Post by Jaygan on 2010-05-03
That worked wonderfully oldfred, I have the results.txt.  The output is rather long, should I post the whole thing?

---

### Post by oldfred on 2010-05-03
Please post it all but use the code tags so it is in scroll box. as you paste it it still should be highlighted and click on the # (right side of edit panel above your entry. Or highlight with mouse and click on code tags.

If you hover mouse over # you will see what it does.

---

### Post by Jaygan on 2010-05-03
Thanks, here is the results:

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18387c7d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  12 Compaq diagnostics
/dev/sda2    *     12,595,200   201,663,944   189,068,745   7 HPFS/NTFS
/dev/sda3         201,663,945   390,716,864   189,052,920   5 Extended
/dev/sda5         201,664,008   382,941,404   181,277,397  83 Linux
/dev/sda6         382,941,468   390,716,864     7,775,397  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        220CFF700CFF3D7B                       ntfs                                     
/dev/sda2        36DC9074DC90305B                       ntfs                                     
/dev/sda5        43fa69d2-af89-44b3-b49b-600eedb5de25   ext4                                     
/dev/sda6        9f37ae79-08b0-4417-be22-3fb924f9a4bc   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
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
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 43fa69d2-af89-44b3-b49b-600eedb5de25
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 220cff700cff3d7b
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 36dc9074dc90305b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

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
UUID=43fa69d2-af89-44b3-b49b-600eedb5de25 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9f37ae79-08b0-4417-be22-3fb924f9a4bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 107.1GB: boot/grub/core.img
 106.4GB: boot/grub/grub.cfg
 103.8GB: boot/initrd.img-2.6.31-14-generic
 104.1GB: boot/initrd.img-2.6.31-20-generic
 104.4GB: boot/initrd.img-2.6.31-21-generic
 103.8GB: boot/vmlinuz-2.6.31-14-generic
 104.0GB: boot/vmlinuz-2.6.31-20-generic
 104.3GB: boot/vmlinuz-2.6.31-21-generic
 104.4GB: initrd.img
 104.1GB: initrd.img.old
 104.3GB: vmlinuz
 104.0GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by oldfred on 2010-05-04
I cannot see anything in you results.txt that looks wrong. Maybe someone else will.

Are you booting the correct windows entry, sda1 XP is just a recovery partition. the Vista on sda2 has the boot flag is looks like it has all your files.

If the Vista does not work:
You might try manual booting with the e on the Vista entry and totally delete the line starting with search. then boot.

---

### Post by Jaygan on 2010-05-04
I am booting into Vista.  I have no clue how to manual boot etc.

---

### Post by oldfred on 2010-05-04
Your original post said windows did not work, so now it does. Are we done?

---

### Post by Jaygan on 2010-05-04
I was clarifying that I was using sda2 to attempt to boot up windows, it is still unsuccesful.  Sorry for the miscommunication.  My computer still restarts when I select windows.

---

### Post by oldfred on 2010-05-04
Lets test this:
From the grub menu, scroll to the Vista entry, use e for edit and remove the entire search line, then boot.

---

### Post by Jaygan on 2010-05-05
I deleted the line, but is there something I have to do to save that change?  When I boot after deleting it my computer restarts and when I return to the edit screen for Vista the search line is there again.

---

### Post by oldfred on 2010-05-05
Did it work with the line deleted?

This has instuctions on modifing code:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

But I prefer to just copy the windows stanza to 40_custom and edit it.

IF the new entry works then you can turn off os prober so it does not find windows. (if you ever add another system turn it on to get auto update)

In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

Find current entry:
gedit /boot/grub/grub.cfg
Copy entry to here:
gksudo gedit /etc/grub.d/40_custom
Edit /etc/default/grub
gksudo gedit /etc/default/grub
sudo update-grub


after any changes:
sudo update-grub

---

### Post by Jaygan on 2010-05-05
Deleting the search line still wont let me into windows.  Forgive my ignorance, but how one I find the current entry how do I copy it to the specified location>

---

### Post by oldfred on 2010-05-05
If it did not work then you do not need to copy the entry. I thought that worked for you so we wanted that as the standard.

While your windows looks ok. I would reinstall the windows boot loader to the MBR and see if it boots. If not run a full set of repairs using the windows CD. Reboot & make sure windows boots ok.
Then reinstall grub and run sudo update-grub to make sure it finds the fixed windows.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

To reinstall grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Jaygan on 2010-05-05
Success!  Thank you very much my friend. :)

---

### Post by oldfred on 2010-05-06
Glad you got it working. Even though script did not show it there must have been some issue with windows.

---

