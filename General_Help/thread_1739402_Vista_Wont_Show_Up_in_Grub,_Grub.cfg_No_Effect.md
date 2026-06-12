---
title: "Vista Wont Show Up in Grub, Grub.cfg No Effect"
date: 2011-04-25
forum: General Help
---

### Post by belikerob on 2011-04-25
Hello ubuntu forums, Last night I dual booted Vista and ubuntu on my computer. Install went fine and I went to bed after it finished. This morning when I turned on my computer I realized vista wasn't an option in grub. I used sudo fdisk -lu and realized vista was still installed. I tried to edit the menu.lst file but realized I was on a newer version. I retried in grub.cfg and no effect. I tried yet another time by going through etc and then updating the grub. Nothing has worked. I took a couple pics to help everyone better understand. How do I add vista to the grub start-up? Thanks in advance
[U][B]
fdisk:[/B][/U](appears to still be installed on sda3, a4 is ubuntu)[U][B]
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/fdisk.jpg[/IMG]


Grub.cfg:[/B][/U] (I put the commands in)[U][B]

[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/grubcfg.jpg[/IMG]

Grub:[/B][/U] (no vista)[U][B]

[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/grub.jpg[/IMG]


MemTest:[/B][/U] (tried running it out of curiosity, end of scan it said 0 issues)
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/memtest86.jpg[/IMG]

---

### Post by Quackers on 2011-04-25
Welcome to UF.
I am unsure whether you have run ```
sudo update-grub
``` in a terminal, have you?
If you have already done that please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by belikerob on 2011-04-25
Thanks for helping, I was afraid no one would respond. yea I tried the update much earlier today. Here's the results...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              98,304    13,526,729    13,428,426  82 Linux swap / Solaris
/dev/sda3    *     13,526,730   873,835,685   860,308,956   7 HPFS/NTFS
/dev/sda4         873,836,544   976,771,071   102,934,528  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 33 MB, 33030144 bytes
2 heads, 32 sectors/track, 1008 cylinders, total 64512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32        64,447        64,416   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0902                              vfat       DellUtility                   
/dev/sda2        5e5d2dcd-a910-4b78-82bd-474113d9b4d3   swap                                     
/dev/sda4        25e32d24-2da4-4330-b4b6-cda638ebdcdf   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        315D-1484                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/315D-1484         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda4/boot/grub/menu.lst: ===========================

title Windows Vista
root (hd0,2)
savedefault
chainloader +1

=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25e32d24-2da4-4330-b4b6-cda638ebdcdf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25e32d24-2da4-4330-b4b6-cda638ebdcdf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
title Windows Vista
root (hd0,2)
chainloader +1
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=25e32d24-2da4-4330-b4b6-cda638ebdcdf /               ext3    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 448.5GB: boot/grub/core.img
 448.5GB: boot/grub/grub.cfg
 448.5GB: boot/grub/menu.lst
 448.5GB: boot/initrd.img-2.6.35-22-generic
 448.5GB: boot/vmlinuz-2.6.35-22-generic
 448.5GB: initrd.img
 448.5GB: vmlinuz
 
```

---

### Post by Quackers on 2011-04-25
A couple of things.
Do you know how you ended up with a /boot/grub/menu.lst in sda4?  As you are using Ubuntu 10.10 there shouldn't be one there.
Your main problem is that sda3 (your Windows partition) is not currently mounting. That's bad.
Before you installed Ubuntu did you resize the C: drive in Windows? If so what program did you use?

---

### Post by belikerob on 2011-04-25
> **Quackers said:**
> A couple of things.
Do you know how you ended up with a /boot/grub/menu.lst in sda4?  As you are using Ubuntu 10.10 there shouldn't be one there.
When I looked up vista not showing in grub, the advice was to edit menu.lst. For about 30 minutes I tried countless variations before i realized ubuntu 10.10 used boot.cfg. I probably saved it or transferred it while messing around.

>  Your main problem is that sda3 (your Windows partition) is not currently mounting. That's bad.
Before you installed Ubuntu did you resize the C: drive in Windows? If so what program did you use?As a matter of fact I did, I didnt think that it might have been related. I used paragon partition manager 10 I believe

---

### Post by Quackers on 2011-04-25
It is possible that it is the reason that sda3 will not mount. Windows Vista/7 does not like other partition tools changing its partitions.
Do you have a Windows Vista/7 repair disc or installation disc?

---

### Post by belikerob on 2011-04-25
Yea its definitely possible, although not too likely I suppose. Ive used the exact same program twice before on the same computer. About a year and a half ago I installed ubuntu, never used it, and uninstalled it a couple weeks later. No previous issues before this morning. 
> Do you have a Windows Vista/7 repair disc or installation disc?
I'm sure I have it somewhere haha, I was just hoping it wouldn't come to that. Would I lose everything on the previous set-up? Everything important is backed up, its just a hassle to re-install/re-download everything you know

---

### Post by Quackers on 2011-04-25
You only lose everything if you re-install. We can try a couple of things first.
First you could try booting from the disc and selecting the recovery/repair  option. You will probably see a window appear saying that it will attempt to automatically repair your system. Use that first, but take notice of whether it actually lists your system in the window. If it does, highlight it and click on repair. It probably won't fix it, but worth a try. Reboot.
If that runs and doesn't fix it (Windows should boot directly if it has) please go back in and select the repair option then the command prompt option. 
In the command prompt window type in ```
chkdsk C: /r
``` and see if that will run.

---

### Post by belikerob on 2011-04-25
Alright, Ill go do that now. It might take a little bit tho

---

### Post by Quackers on 2011-04-25
No problem. Please report any errors, if you get any.

---

### Post by belikerob on 2011-04-26
I put in the disk and started it through bios. It asked me to fill out name/date, i hit next. It gave me the option of install or repair. I clicked repair and it loaded that box, but nothing showed up. 
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/0425112355.jpg[/IMG]

I clicked on load drives and it brought me to my computer, I figured I'd look at the C drive but it wasn't found :(
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/0426110001.jpg[/IMG]



On a related note I remember there being a command i typed earlier today that mentioned mounting. It was advice I got to make vista show in grub, but I dont recall it doing anything. Im sorry I cant remember in more detail. You mentioned that the drive was unmounted though so it could be related.

---

### Post by Quackers on 2011-04-26
Is there an option in the bottom left of the screen for advanced options or repair? Use that and run the chkdsk command quoted earlier in the command prompt please (if it will run).

---

### Post by belikerob on 2011-04-26
I typed that in dos and it started quickly rolling down text, which its been doing for at-least 5 minutes now
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/0426110028a.jpg[/IMG]

---

### Post by Quackers on 2011-04-26
Hmm, all you can do is let it run, really. See what it reports. That's a lot of stuff! 
If it reports errors at the end, please run it again, until no errors are reported.

---

### Post by belikerob on 2011-04-26
Haha yea I didn't expect to see this much. I'm pretty sure I read fixing corrupted files but couldn't grab a pic in time. We'll see when its done I suppose

---

### Post by Quackers on 2011-04-26
Well that's good I suppose :-)

---

### Post by oldfred on 2011-04-26
I do not know if it is a good sign that it is posting that many issues. 

But chkdsk on a larger partition can take hours. Do not interrupt it and we wlll see you tomorrow morning.

You also posted the old style grub legacy entry into 40_custom. You will need to delete that.

title Windows Vista
root (hd0,2)
chainloader +1

If you get Vista working the os-prober will find the Vista entry and automatically add it.

It will look like this:

menuentry "Windows Vista (loader) (on /dev/sda3)" {
insmod ntfs
set root=(hd0,3)
search --no-floppy --fs-uuid --set Vistasda3PartitionUUIDHere
chainloader +1
}

Script/blkid was not able to see UUID for sda3.

---

### Post by Quackers on 2011-04-26
Listen to oldfred - he knows things :-)
Good luck and see you tomorrow! I hope things go well.

---

### Post by belikerob on 2011-04-26
Thanks you guys, I really appreciate the help. I let it run over night and here's what it said this morning. 
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/0426110930.jpg[/IMG]
We're making progress haha

---

### Post by belikerob on 2011-04-26
Should I restart the computer and try to add vista to cfg, or run another test? I'm just gonna wait for confirmation from you guys so I don't jeopardize the scan haha.

---

### Post by oldfred on 2011-04-26
With chkdsk you have to run it until there are no errors as it does not fix everything on one pass. Not sure why you were getting so many messages and then it had too many to copy.

Once chkdsk is clear, then you can reboot into Ubuntu and run this.

```
sudo update-grub
```

If Vista still not found then then there are some advanced repairs with testdisk on NTFS partitions.

---

### Post by belikerob on 2011-04-26
How do I know when there are no more errors?

---

### Post by Quackers on 2011-04-26
You won't get any errors reported and it won't fix anything :-)

---

### Post by belikerob on 2011-04-26
Haha good point :)
Alright alot just happened so sorry for like 7 pics.
I tried to run the repair again and it failed
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/diskfails.jpg[/IMG]

I went into ubuntu and deleted the old code in boot.cfg (the custom startup stuff) then updated
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/update.jpg[/IMG]

When I restarted Grub showed Vista
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/showsgrub.jpg[/IMG]

Then it failed
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/grubfails.jpg[/IMG]

I restarted into vista repair disk and it gave me this
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/showsdrive.jpg[/IMG]

Then failed
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/drivefails.jpg[/IMG]

I re-ran the origional scan (the one you type in command)
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/startscurrent.jpg[/IMG]

Its running right now




Once again, Thanks for the help and sorry for the gigantic pictures

---

### Post by belikerob on 2011-04-26
Running currently
[IMG]http://i279.photobucket.com/albums/kk155/belikerob/ubuntu/currently.jpg[/IMG]

---

### Post by Quackers on 2011-04-26
So Windows is now listed in the grub menu, but when selected it won't boot. Is that correct?
The chkdsk error I expected the first time :-)  Not now.
Windows repair function now realises that Windows is installed, whereas it didn't before. So something's been fixed :-)
See what oldfred thinks. You may need to try to rebuildbcd, then fixmbr.

Oh, I see your newest post. chkdsk is now running again?

---

### Post by belikerob on 2011-04-26
> **Quackers said:**
> So Windows is now listed in the grub menu, but when selected it won't boot. Is that correct?
Yep, I get the screen saying to put the repair disc in


> Oh, I see your newest post. chkdsk is now running again?Yep, its at 75% right now :)

---

### Post by oldfred on 2011-04-26
I would try windows repairs. If you use the auto repair, it is like chkdsk and only does one thing at a time. And one of the auto repair will install windows boot loader to the MBR. That could be ok just to check that windows works. But then you have to reinstall grub2's bootloader to the MBR. Grub will only boot windows if it is a working windows.

I posted the manual commands here from some windows sites.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

If you have to reinstall grub2's boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by belikerob on 2011-04-26
I have tried chkdsk about 5 times now and everytime it doesnt find all the errors :( Startup repair won't run.  Do you think you could go into a little more detail oldfred? Whats the next step, should I just keep running chkdsk or is there another method?

---

### Post by Quackers on 2011-04-26
I'm wondering if your system has been too badly damaged :-(
Multiple chkdsk's is a lengthy job. See how they go.
The Windows error message mentions /Boot/BCD. It is possible to rebuild this file, but doing so seems to have varying results. We also don't know what state your system is in, but it could be worth trying to get it to boot.
To rebuild the BCD file you need to boot from the Windows repair disc and go to the command prompt option.
In the command prompt window enter ```
bootrec.exe /rebuildBCD
``` and if that goes ok we could try fixing the mbr so that just Windows will boot (we can re-install grub later) with this command run from the command prompt window ```
bootrec.exe /fixmbr
```
If no errors are reported, try rebooting and see if Windows can boot.

---

### Post by oldfred on 2011-04-26
Testdisk has some repairs to NTFS. But I think it does not always create a bootable system, so even if it fixes it, you still have to run/rerun the windows repairs.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)


Windows also has another set of commands ( not sure why).
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by belikerob on 2011-04-27
> bootrec.exe /rebuildBCD
I got "Succesfully scanned windows installations.
Total identified windows installations: 0
The operation completed sucessfully

---

### Post by oldfred on 2011-04-27
From Ubuntu can you mount/see the NTFS partition now. If so run this so we can see what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by belikerob on 2011-04-27
Thanks for the help fred, do you think its fixable?
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 31555584. But according to the info from 
                       fdisk, sda3 starts at sector 13526730.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb1 has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2              98,304    13,526,729    13,428,426  82 Linux swap / Solaris
/dev/sda3    *     13,526,730   873,835,685   860,308,956   7 HPFS/NTFS
/dev/sda4         873,836,544   976,771,071   102,934,528  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 33 MB, 33030144 bytes
2 heads, 32 sectors/track, 1008 cylinders, total 64512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32        64,447        64,416   4 FAT16 <32M


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0902                              vfat       DellUtility                   
/dev/sda2        5e5d2dcd-a910-4b78-82bd-474113d9b4d3   swap                                     
/dev/sda3        441A2E5B1A2E49EE                       ntfs                                     
/dev/sda4        25e32d24-2da4-4330-b4b6-cda638ebdcdf   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        315D-1484                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/4_27_2011         udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb1        /media/315D-1484         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda3        /media/441A2E5B1A2E49EE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/menu.lst: ===========================

title Windows Vista
root (hd0,2)
savedefault
chainloader +1

=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25e32d24-2da4-4330-b4b6-cda638ebdcdf ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25e32d24-2da4-4330-b4b6-cda638ebdcdf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 25e32d24-2da4-4330-b4b6-cda638ebdcdf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 441a2e5b1a2e49ee
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=25e32d24-2da4-4330-b4b6-cda638ebdcdf /               ext3    errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 448.5GB: boot/grub/core.img
 448.5GB: boot/grub/grub.cfg
 448.5GB: boot/grub/menu.lst
 448.5GB: boot/initrd.img-2.6.35-22-generic
 448.5GB: boot/vmlinuz-2.6.35-22-generic
 448.5GB: initrd.img
 448.5GB: vmlinuz

```

---

### Post by oldfred on 2011-04-27
Boot flag and two of the three files required to boot windows are in sda3. But the script is not showing this essential file. I have seen script just not pick it up. Can you check if it is in your windows partition. It is normally part of the main windows partition.

/Windows/System32/winload.exe

Win7 often has these two separate in a boot/recovery partition which you do have and with Vista all three are in one main partition:
/bootmgr /Boot/BCD

If you do multiple installs of windows it moves boot files to the one active partition (boot flag).

---

### Post by belikerob on 2011-04-28
Sorry, that went a little over my head. What file am I looking for and which directory would it be in? I'm on vista btw

---

### Post by xNaughx on 2011-04-28
He just wants to know if these files(3) are in your Windows partition (C:\ by default)

C:\Windows\System32\winload.exe

C:\bootmgr

C:\Boot\BCD


*Windows 7 got a separate partion of around 100 mb named "System Reserved" that's why. (but not on Vista)

Some of theses files are in that partition on Win 7

---

### Post by belikerob on 2011-05-01
Alright,   "C:\Boot\BCD"  and    "C:\bootmgr"    both exist. However, "C:\Windows\System32\winload.exe"   seems to have disappeared. It is not in system32, it is completely absent.

---

### Post by oldfred on 2011-05-01
the c:\windows and the c:\windows\system & c:\windows\system32 are your windows install (plus programs and lots of other folders). If those are missing you have lost windows.

---

### Post by belikerob on 2011-05-01
> **oldfred said:**
> the c:\windows and the c:\windows\system & c:\windows\system32 are your windows install (plus programs and lots of other folders). If those are missing you have lost windows.

Well, I have both of those folders. Its just that particular file I'm missing

---

### Post by oldfred on 2011-05-01
If that is the only file missing it may be repairable, but I do not think that is a file normally restored with repairs. 

You may want to check in the windows forums or search. You may have a backup hidden somewhere on you system also.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

