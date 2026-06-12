---
title: "Installed Ubuntu on my Windows laptop and it worked until I restarted..."
date: 2010-12-04
forum: General Help
---

### Post by MaestroDT on 2010-12-04
I have a Dell e1505 that originally had Windows XP Pro installed. I want to learn Linux so I installed Ubuntu... during disc partitioning I used "side by side" or something for the installation... I think the general idea was that it resized my existing OS partition, which was NTFS.

After installation, it booted up and worked fine... I had it on for a day and restarted it today and it won't work. I get the regular Windows bootloader, not grub or whatever Linux uses. It gives me the option of Windows XP or Ubuntu. Windows will still load, but if I select Ubuntu, it gives me the following error:

Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): Extended:
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd0,4): EXT2: _

The "_" is where the flashing cursor is. It won't let me type anything, if I hit more than like 10 keys, it starts beeping everytime I hit any key. 

How can I get Ubuntu working again? I was really enjoying it but I really don't feel like going through the entire installation again.

---

### Post by oldfred on 2010-12-04
So we can see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by MaestroDT on 2010-12-04
Can I do that from a LiveCD?

---

### Post by oldfred on 2010-12-04
Sure, but it will not be saved once you reboot unless you copy the file to an external device.

Just directly post the results.txt from the liveCD as the instructions discuss.

---

### Post by MaestroDT on 2010-12-04
Ok, here's my results.

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   128,795,486   128,795,424   7 HPFS/NTFS
/dev/sda2         128,796,670   312,580,095   183,783,426   5 Extended
/dev/sda5         128,796,672   306,440,191   177,643,520  83 Linux
/dev/sda6         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       be29dd1d-9a63-488f-973a-c4475195882c   ext4                                     
/dev/sda1        D8F87834F87812CC                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8901e9e8-d856-43fd-bcaf-178fe8be15be   ext4                                     
/dev/sda6        b0abc89e-e00c-45d5-adf6-63b6358dcc27   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 8901e9e8-d856-43fd-bcaf-178fe8be15be
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 8901e9e8-d856-43fd-bcaf-178fe8be15be
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8901e9e8-d856-43fd-bcaf-178fe8be15be
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8901e9e8-d856-43fd-bcaf-178fe8be15be ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8901e9e8-d856-43fd-bcaf-178fe8be15be
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8901e9e8-d856-43fd-bcaf-178fe8be15be ro single 
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8901e9e8-d856-43fd-bcaf-178fe8be15be
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 8901e9e8-d856-43fd-bcaf-178fe8be15be
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d8f87834f87812cc
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8901e9e8-d856-43fd-bcaf-178fe8be15be /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b0abc89e-e00c-45d5-adf6-63b6358dcc27 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  68.2GB: boot/grub/core.img
 124.0GB: boot/grub/grub.cfg
  66.7GB: boot/initrd.img-2.6.35-22-generic
  68.2GB: boot/vmlinuz-2.6.35-22-generic
  66.7GB: initrd.img
  68.2GB: vmlinuz
```

---

### Post by oldfred on 2010-12-04
Your wubi looks like it has issues, are/were you still using it?

It looks like you should be be able to reinstall grub to the MBR.

#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by MaestroDT on 2010-12-04
That's the thing though... I don't think I ever installed wubi. I definitely didn't install it on my Windows partition. Unless the Ubuntu 10 CD installer installs wubi with the "side by side with my operating system" install, then I never had it in there.

So... what's the deal with that?

---

### Post by oldfred on 2010-12-04
Just boot into windows and see if you can uninstall it. It should uninstall like another windows program.

If issues:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

### Post by MaestroDT on 2010-12-05
I installed Linux MINT and used "side by side" with my ubuntu partition.

Everything works now. Now grub comes up instead of windows boot loader.

---

### Post by MaestroDT on 2010-12-05
Okay, so it apparently did install wubi because I have a "ubuntu" program on Windows and a ubuntu folder under my C: directory.

HOWEVER, I also now have a 40GB partition with Ubuntu installed and now a 42GB partition with Mint installed. Windows is installed on a 60GB partition.

SO, why did Ubuntu installer install Wubi AND a separate partition install? I don't get it. Wubi has it's own disk files and stuff, its a totally self contained installation on my windows partition, but it also made a 40GB partition.

How can I tell if Ubuntu is running from Wubi or from the 40GB partition? I don't want it running from Wubi... I don't like Wubi.

---

### Post by oldfred on 2010-12-05
The boot script only showed Ubuntu 10.10 in sda5. Did you install Mint after you ran the script?

I have never installed wubi so I am not familiar with how it installs, but you can create a second NTFS partition and install to that, but that is not common. If you have nothing in wubi just delete it from windows.

---

