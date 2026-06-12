---
title: "Invisible ubuntu 10.10"
date: 2010-12-08
forum: General Help
---

### Post by larswebb on 2010-12-08
Hi everyone,

  I just installed ubuntu 10.10 along side w7. Everything went well through the install and the ubuntu disk ejected. Then the screen filled with i/o errors. So I rebooted and the boot menu shows xp and w7 but no ubuntu. Using easeus partition manager it shows the xp and w7 partition but where the ubuntu partition should be it shows "other". The w7 partition is reduce by the amount I specified for ubuntu. So hopefully it's there and I can find it. I tried installing twice with the same result.
 The XP partition is shrunk to a min. and not used anymore.

Any help will be greatly appreciated

Thanks,
Larry


Win XP pro/Win7
i5 2.67
4g ram
Seagate 250 sata
Seagate 750 sata (storage)

---

### Post by sikander3786 on 2010-12-08
Welcome to the forums :-)

I suspect you installed Ubuntu inside Windows using Wubi installer (??).

We need to see the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

You will need to boot and Ubuntu Live CD/USB for that. It would tell us more about your setup.

Please wrap your output with proper code tags from post menu. Press # and paste your text in between the generated code tags.

---

### Post by larswebb on 2010-12-08
Hi, thanks for the reply! I had ubuntu inside windows 7 before and I liked it so now I installed it in it's own partition. Maybe I'll go back to the wubi inside windows it was a lot less trouble. But i'd prefer to do it the right way.
I'll try that bootinfoscript when i get home.

Thanks,

larry

---

### Post by larswebb on 2010-12-08
Well I thought I'd had a good idea and deleted the new partition. I then re-sized my XP partition to be larger than Win7. So I tried to install ubuntu next to XP this time, and the same thing happened. So I restored from a backup and now I'm back to using ubuntu inside Win7. I really don't want XP at all, and I now there is a way to just put ubuntu in it's place but I am struggling. I thought this would be easy. I am going to search for a to tutorial about replacing XP with ubuntu.

---

### Post by Quackers on 2010-12-08
If you still need help we need the output of the boot script that Sikander3786 asked for. Otherwise we're guessing!

---

### Post by larswebb on 2010-12-08
ok, I am back to using ubuntu inside win7 again. These are the results of the script. I will try installing to a partition and run the script again if necessary.

 Thanks for taking the time to help me out.

---

### Post by sikander3786 on 2010-12-08
That is the script itself :-)

You need to download the script to your desktop, and run this command from Terminal.

```
sudo bash ~/Desktop/boot_info_script*.sh
```

It would generate a Results.txt on your desktop. Copy/paste text from that file in your post.

If you are satisfied with your setup at the moment (as you've re-installed everything), we would not force you to post it anyway ;-)

---

### Post by bcbc on 2010-12-09
Just be careful wiping XP. When you install Win 7 after XP, it places the Win 7 boot files on the XP partition. [http://www.multibooters.co.uk/system.html](http://www.multibooters.co.uk/system.html)

---

### Post by larswebb on 2010-12-09
[FONT=monospace]Ok here it is.  
            

      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader? is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,126 1,465,144,064 1,465,127,939   f W95 Ext d (LBA)
/dev/sda5              16,189 1,465,144,064 1,465,127,876   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   178,128,719   178,128,657   7 HPFS/NTFS
/dev/sdb2         178,128,720   488,392,064   310,263,345   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 64 MB, 64487424 bytes
4 heads, 32 sectors/track, 984 cylinders, total 125952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32       125,823       125,792   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       1fa5a1ea-c1ce-4cea-b07c-49cd1e9f8fea   ext4                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda5        01CADFF75E324770                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BA50E45F50E423BB                       ntfs       Windows XP Pro x86            
/dev/sdb2        AEA61EEFA61EB7B3                       ntfs       Windows 7 Ultimate            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        18E2-2763                              vfat       REAR USB                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc1        /media/REAR USB          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sdb2/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-23-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set aea61eefa61eb7b3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic-pae root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-23-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set aea61eefa61eb7b3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic-pae root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-22-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set aea61eefa61eb7b3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic-pae root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, Linux 2.6.35-22-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set aea61eefa61eb7b3
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic-pae root=/dev/sdb2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda5)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 01cadff75e324770
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

============================= sdb2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb2/Wubi: Location of files loaded by Grub: =================


  15.3GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic-pae
    .7GB: boot/initrd.img-2.6.35-23-generic-pae
  13.2GB: boot/vmlinuz-2.6.35-22-generic-pae
  13.2GB: boot/vmlinuz-2.6.35-23-generic-pae
    .7GB: initrd.img
    .5GB: initrd.img.old
  13.2GB: vmlinuz
  13.2GB: vmlinuz.old[/FONT]

---

### Post by mastablasta on 2010-12-09
doesn't seem like you have any linux installed. only wubi.
 
you need to install linux on an empty partition.
 
here is how you do it: [http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/)
 
For Ubuntu 10.04 you can find instructions here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Page 11 onwards i believe...

---

### Post by larswebb on 2010-12-09
Can I keep my wubi installation too?

  What's better, the automatic option to install ubuntu next to another OS or choose manual (advanced) and install on separate partition. Manual requires me to choose the partition and the boot loader. Also if I create a partition what should I format it as?

---

### Post by larswebb on 2010-12-10
I re-installed ubuntu and got rid of XP. The install went well again and ubuntu is taking up space, but I can't see it or boot to it. Here's the results of the bootscript.
 Thanks to bcbc and Greg Shultz for helping me get rid of XP.

---

### Post by bcbc on 2010-12-10
You've installed grub2's bootloader on /dev/sda, but you're probably booting from /dev/sdb, which has windows as it's bootloader.

So, boot from a live CD, and install grub to /dev/sdb:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

---

### Post by Slinkee2k on 2010-12-10
What **bcbc **said.^ That SHOULD be pretty easy/simple to do, though I'm not familiar with how to install *only* grub2 from the boot disk. You will want to "/dev/sdb" as **bcbc** said above.

Alternatively, if you can't seem to install grub2 to your hard drive that has Windows on it, you may be able to just tell your  computer (in the BIOS) to **boot to the other physical hard drive **(the one  with Linux on it **instead **of the Windows one). If you do this, let's see if it boots!

However, please note that while your grub2 should boot to Linux nicely, it might not be set up with an option to boot to Windows that's on the other drive.

In Linux, you can edit the grub2 configuration file found here: /boot/grub/grub.cfg
Before editing it, you should ALWAYS make a backup copy of it.
```
$ cd /boot/grub *#! changes to the /boot/grub directory* (folder)
$ cp -i grub.cfg grub.cfg.backup *#! copies grub2 config file, and check for overwrite (DON'T OVERWRITE FILES UNLESS YOU KNOW WHAT YOU'RE DOING) ;P*
$ sudo gedit grub.cfg* #! this opens the grub2 config in gedit text editor. Make sure you saved a backup before editing grub.cfg*
```You would then add an entry to boot to Windows on /dev/sdb. I don't know how the entry would be structured, and I can't check mine right now, I'm at work. LoL.

---

### Post by larswebb on 2010-12-10
I followed bcbc advice and now I can boot to ubuntu. I used startup manager to to make win7 my default. The boot screen is kind of messy with extra options,  Ubuntu first and win7 last but it works fine. I still can't see the ubuntu partition in windows or with easeus partition manager. Windows doesn't show anything and easeus shows "other", I cannot rename it . I've attached what gparted shows. Everything is working fine and I'll leave it at that for now.
  Why is xp still in the boot script results? see attachment.

Thanks a bunch,
Larswebb

---

### Post by bcbc on 2010-12-10
Startup-manager is easy to set, but it's a fixed menu number - so if you install a new kernel, you'll find you're booting the memory check or something else.

If you want to default to Windows, there are a few options. A one-stop shop for this is drs305's [grub2 title tweaks]("http://ubuntuforums.org/showthread.php?t=1287602"). 

I've used meierfra's custom menu at one time (link given in that thread) as well as some of the other tricks... e.g. limiting kernels shown, removing memory check and windows recovery as a boot option, and setting Windows to be the first (& default) menu entry.

You can also uninstall kernels from Synaptic to reduce clutter, but I strongly recommend keeping at least 2 working kernels where possible.

---

