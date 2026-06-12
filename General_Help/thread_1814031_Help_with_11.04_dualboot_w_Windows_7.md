---
title: "Help with 11.04 dualboot w/ Windows 7?"
date: 2011-07-28
forum: General Help
---

### Post by JordanMS on 2011-07-28
Hi :)
I've been trying to dual boot with Windows 7.
I installed it on my backup harddrive. I've tried booting it from there but no luck. 
And I'm not seeing a boot from message.
Help? :(

---

### Post by lmarmisa on 2011-07-28
Welcome to the forums. :D

Are you able to boot into Windows 7?.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Welcome to the forums. :D

Are you able to boot into Windows 7?.

Thank you. :) and yes, I'm on Windows 7 right now on the same computer.

---

### Post by lmarmisa on 2011-07-28
Did you install the GRUB loader of Ubuntu on the MBR of your backup harddrive?.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Did you install the GRUB loader of Ubuntu on the MBR of your backup harddrive?.
Nope. Never heard of it. xD
I'm sorry for my noobyness I haven't  ran Ubuntu in a while.

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> Nope. Never heard of it. xD
I'm sorry for my noobyness I haven't  ran Ubuntu in a while.

No problem. :)

Do you know if you installed Ubuntu by means of Wubi?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Or did you boot into an Ubuntu Live CD for the installation?.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> No problem. :)

Do you know if you installed Ubuntu by means of Wubi?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Or did you boot into an Ubuntu Live CD for the installation?.

I booted from a CD. I selected run along with Windows 7.
And I see wubi in my backup harddrive.
If I run it. Will it override Windows 7?

---

### Post by aka120 on 2011-07-28
I used EasyBCD to set up my dual boot. It's very simple and Windows 7 remains your bootloader giving you the choice of booting to Windows 7 or Ubuntu. The guide is here
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

If you prefer the Grub loader to be your boot menu then someone here can help you with it, I've done it several times but its been a while.

*If your motherboard has a boot choice menu, you can simply select which hdd to boot to as well, but this is not really good for dual booting, it is a workaround though so it helps to have that option sometimes.

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> I booted from a CD. I selected run along with Windows 7.
And I see wubi in my backup harddrive.

Oops. Ubuntu with Wubi is installed while you run Windows. 

Did you use an install menu similar to the image attached to my previous post?.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Oops. Ubuntu with Wubi is installed while you run Windows. 

Did you use an install menu similar to the image attached to my previous post?.

I just burned the cd. Installed it and restarted. And it booted with Windows 7. :l
-_-

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> I just burned the cd. Installed it and restarted. And it booted with Windows 7. :l
-_-

Ok. I recommend to run the Boot Info Script. This script searches information about your system in order to fix boot problems.

Please, boot into an Ubuntu Live CD (or USB), select Try Ubuntu, open Firefox and go to the page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions of the page for downloading and running the script. Finally post the results on this thread.

I hope this procedure will be not too difficult.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Ok. I recommend to run the Boot Info Script. This script searches information about your system in order to fix boot problems.

Please, boot into an Ubuntu Live CD (or USB), select Try Ubuntu, open Firefox and go to the page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions of the page for downloading and running the script. Finally post the results on this thread.

I hope this procedure will be not too difficult.

Will try. thanks. :)

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Ok. I recommend to run the Boot Info Script. This script searches information about your system in order to fix boot problems.

Please, boot into an Ubuntu Live CD (or USB), select Try Ubuntu, open Firefox and go to the page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions of the page for downloading and running the script. Finally post the results on this thread.

I hope this procedure will be not too difficult.
There's 2 file. a .sh and a changelog file . Which one do I copy and paste?

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> There's 2 file. a .sh and a changelog file . Which one do I copy and paste?

CHANGELOG is not important.

The only important file is **boot_info_script.sh**.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> CHANGELOG is not important.

The only important file is **boot_info_script.sh**.

The results are in.
This is what I get :
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,224,962,047 1,224,755,200   7 NTFS / exFAT / HPFS
/dev/sda3       1,224,962,048 1,250,260,991    25,298,944   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,516,330,036 1,516,329,974   7 NTFS / exFAT / HPFS
/dev/sdb2       1,516,331,006 1,953,523,711   437,192,706   5 Extended
/dev/sdb5       1,516,331,008 1,947,758,591   431,427,584  83 Linux
/dev/sdb6       1,947,760,640 1,953,523,711     5,763,072  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EE34BCCB34BC97D3                       ntfs       SYSTEM
/dev/sda2        B614BE0014BDC3A1                       ntfs       OS
/dev/sda3        6CDE3EB2DE3E7504                       ntfs       HP_RECOVERY
/dev/sdb1        A43CCF4F3CCF1B66                       ntfs       FreeAgent Drive
/dev/sdb5        9b384743-7f8e-48ce-8bcc-9578055375f9   ext4       
/dev/sdb6        30332b70-599c-4bac-8fe0-a7fb47937763   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 9b384743-7f8e-48ce-8bcc-9578055375f9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 9b384743-7f8e-48ce-8bcc-9578055375f9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 9b384743-7f8e-48ce-8bcc-9578055375f9
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9b384743-7f8e-48ce-8bcc-9578055375f9 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 9b384743-7f8e-48ce-8bcc-9578055375f9
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9b384743-7f8e-48ce-8bcc-9578055375f9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 9b384743-7f8e-48ce-8bcc-9578055375f9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 9b384743-7f8e-48ce-8bcc-9578055375f9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root EE34BCCB34BC97D3
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root B614BE0014BDC3A1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 6CDE3EB2DE3E7504
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=9b384743-7f8e-48ce-8bcc-9578055375f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=30332b70-599c-4bac-8fe0-a7fb47937763 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 871.177001953 = 935.419183104  boot/grub/core.img                             1
 737.226207733 = 791.590612992  boot/grub/grub.cfg                             1
 757.878906250 = 813.766279168  boot/initrd.img-2.6.38-8-generic               2
 871.175273895 = 935.417327616  boot/vmlinuz-2.6.38-8-generic                  1
 757.878906250 = 813.766279168  initrd.img                                     2
 871.175273895 = 935.417327616  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by lmarmisa on 2011-07-28
OK. Everything looks good. Ubuntu was installed on the backup hard drive (**/dev/sdb**) and the GRUB boot loader was stored on the MBR of this hard drive.

You have to enter the BIOS menu and go the the boot setting configuration. Then select your backup drive as first priority boot device. Save changes and exit.

You should be able to boot into Ubuntu after this change.

Ubuntu has not modified your Windows loader located on your main hard drive. I like it.

An additional question: is your backup hard drive internal or external?.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> OK. Everything looks good. Ubuntu was installed on the backup hard drive (**/dev/sdb**) and the GRUB boot loader was stored on the MBR of this hard drive.

You have to enter the BIOS menu and go the the boot setting configuration. Then select your backup drive as first priority boot device. Save changes and exit.

You should be able to boot into Ubuntu after this change.

Ubuntu has not modified your Windows loader located on your main hard drive. I like it.

An additional question: is your backup hard drive internal or external?.

How do I edit BIOS?
And external.

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> How do I edit BIOS?
And external.

You have to reboot your system. There is no standard key for the access to the BIOS menu. Watch for a "entering setup" message in the first few seconds after turning on your computer. **F2** and **Del** are common ways to enter BIOS, but it depends on the BIOS manufacturer.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> You have to reboot your system. There is no standard key for the access to the BIOS menu. Watch for a "entering setup" message in the first few seconds after turning on your computer. **F2** and **Del** are common ways to enter BIOS, but it depends on the BIOS manufacturer.

I'm running an HP Pavilion Slimline s5610f

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> I'm running an HP Pavilion Slimline s5610f

My son has an HP Compaq computer more or less similar to yours. In this case, if you press **Escape** at start-up you are able to select the boot device for that time.

Typing **F10**, you enter the BIOS menu.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> My son has an HP Compaq computer more or less similar to yours. In this case, if you press **Escape** at start-up you are able to select the boot device for that time.

Typing **F10**, you enter the BIOS menu.

I found it.
I see a boot folder and 4 options...I don't know what to do. >_<

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> I found it.
I see a boot folder and 4 options...I don't know what to do. >_<

Did you use F10?. Could you give more information about the 4 options?.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Did you use F10?. Could you give more information about the 4 options?.

I see a "BOOT" Option in BIOS. Here. Let me take a picture of it.

---

### Post by lmarmisa on 2011-07-28
Go to the **Boot** menu and select **HDD Group Boot Priority**. Then define your external HDD as the first device.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Go to the **Boot** menu and select **HDD Group Boot Priority**. Then define your external HDD as the first device.

I do that but when I boot it says there's no such partition. :l

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> I do that but when I boot it says there's no such partition. :l

Hmmm. The data shown by Info Boot Script look good. Could you give me more information about the non-existing partition?. What is the exact message shown by Ubuntu?.

You could try to reinstall GRUB but the data seem good.

I suppose the installation ended with no apparent problems.

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Hmmm. The data shown by Info Boot Script look good. Could you give me more information about the non-existing partition?. What is the exact message shown by Ubuntu?.

You could try to reinstall GRUB but the data seem good.

I suppose the installation ended with no apparent problems.
That's all I can see. Mt screen cuts off the rest of the message.

---

### Post by lmarmisa on 2011-07-28
> **JordanMS said:**
> That's all I can see. Mt screen cuts off the rest of the message.

Well. My last attempt. Try to reinstall GRUB2. The reference to the method is this: 

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

These are the steps to follow in your case.

Boot into an Ubuntu Live CD / USB. Try Ubuntu. Open a terminal and type these commands (try to use copy & paste in order to avoid mistakes):

```

sudo mount /dev/sdb5 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
grub-install /dev/sdb
grub-install --recheck /dev/sdb
exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt

```

Finally reboot your system from your external hard drive.

A last question: are you able to select the boot device typing **Escape** at start-up?.

Best regards,

Luis

---

### Post by JordanMS on 2011-07-28
> **lmarmisa said:**
> Well. My last attempt. Try to reinstall GRUB2. The reference to the method is this: 

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

These are the steps to follow in your case.

Boot into an Ubuntu Live CD / USB. Try Ubuntu. Open a terminal and type these commands (try to use copy & paste in order to avoid mistakes):

```

sudo mount /dev/sdb5 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
grub-install /dev/sdb
grub-install --recheck /dev/sdb
exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt

```Finally reboot your system from your external hard drive.

A last question: are you able to select the boot device typing **Escape** at start-up?.

Best regards,

Luis

I can't get it.
I think the best thing to do is actually partition a hard drive.
Anyone know any free partitionaning tools for PC?

---

### Post by lmarmisa on 2011-07-29
> **JordanMS said:**
> I can't get it.
I think the best thing to do is actually partition a hard drive.
Anyone know any free partitionaning tools for PC?

I have an external HDD with an Ubuntu installation very similar to your case and it works just fine. I love it because I can run that Ubuntu in any computer.

I am not able to diagnose your problem precisely. Maybe if you could give a little more details it would be possible.

If you are not an expert in Ubuntu, I do not recommend to install Ubuntu side by side with Windows 7 at the moment. If your current problems continue with the dual boot installation, you could get problems booting into Windows 7 too.  

So I recommend to install Ubuntu with Wubi or install Ubuntu as a virtual machine using [VirtualBox]("http://www.virtualbox.org/"). These two alternatives do not require any change in partitions and have no risk about booting problems. Learn Ubuntu with this installation and get some expertise. Then you will be able to create your own dual boot install safely.

[http://www.youtube.com/watch?v=iW1V6TuZZmc](http://www.youtube.com/watch?v=iW1V6TuZZmc)

[http://www.youtube.com/watch?v=utvM7Zu7zFg](http://www.youtube.com/watch?v=utvM7Zu7zFg)

In relation with the last video, the installation of the VirtualBox GuestAdditions can be made more easily.

Best regards,

Luis

---

