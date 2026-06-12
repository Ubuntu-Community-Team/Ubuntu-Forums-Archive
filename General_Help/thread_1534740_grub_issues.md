---
title: "grub issues"
date: 2010-07-20
forum: General Help
---

### Post by agent_509 on 2010-07-20
I have/had 3 partitions on my hard drive, windows xp, backtrack 4, and ubuntu 10.04 LTS, and installed them in that order (which means Im using the grub from ubuntu) I delted the bt4 partition, only to find that this somehow messed up my grub. 
I've tried several solutions on the internet, but the best i've been able to do is turn my 'grub rescue' command line into the 'grub minimal bash-like' or something like that. How can I fix this?

---

### Post by utnubuuser on 2010-07-20
using a liveCD re-install grub

---

### Post by agent_509 on 2010-07-20
like i said I already tried other solutions on the internet (like reinstalling grub.) and it didn't fix it. There should be no reason grub needs reinstalling anyways because I didnt do anything with my ubuntu partition.

---

### Post by spydeyrch on 2010-07-20
When you say that you messed up your GRUB, what exactly is messed up about it? Give some more details please.  :D

-Spydey :KS

---

### Post by OU_Guy on 2010-07-20
you could use an xp cd and use that to fix the mbr, and from there you can manually setup the other boot options. Or use wubi to install ubuntu again and delete the old one.

---

### Post by philinux on 2010-07-20
> **agent_509 said:**
> I have/had 3 partitions on my hard drive, windows xp, backtrack 4, and ubuntu 10.04 LTS, and installed them in that order (which means Im using the grub from ubuntu) I delted the bt4 partition, only to find that this somehow messed up my grub. 
I've tried several solutions on the internet, but the best i've been able to do is turn my 'grub rescue' command line into the 'grub minimal bash-like' or something like that. How can I fix this?

From the livecd download and run this script. Post back the results.txt file.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by agent_509 on 2010-07-20
Im really looking for a way to fix this from a live cd. I really dont want to reinstall Ubuntu since Im using it as my primary OS and I have lots of programs and files already on it.

---

### Post by spydeyrch on 2010-07-20
I think that more details would allow us to better assess the issue and recommend better solutions.

Are you able to boot into Ubuntu? What about XP? :p I am assuming that you are not but I just want to make sure.

-Spydey :KS

---

### Post by oldfred on 2010-07-20
So we can see where everything is at.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by agent_509 on 2010-07-20
> **philinux said:**
> From the livecd download and run this script. Post back the results.txt file.
 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
 
ok, i'll do that once gparted is done with what it's doing. (cant mount the partition right now)

---

### Post by agent_509 on 2010-07-20
ok, here's all the details I have. I was tripple booting windows xp, backtrack 4, and ubuntu 10.04 LTS. I decided to get rid of BT4 to make room on my hard drive, so I went into a live cd and deleted it. Now for some reason, when I boot up, all i get is the 'grub rescue' message, which i shouldnt get, because I installed Ubuntu last, so if I'm right, then the grub  that Im using is on my Ubuntu partition. I tried to reinstall grub, but now all I have when i boot up is the 'grub minimal bash-like command line' thing. That's all I can think to give you.

---

### Post by agent_509 on 2010-07-20
also, btw, Im not sure how to run that file. given to me earlier

---

### Post by agent_509 on 2010-07-20
how do you run .sh files?

---

### Post by Don1500 on 2010-07-20
> **agent_509 said:**
> ok, here's all the details I have. I was tripple booting windows xp, backtrack 4, and ubuntu 10.04 LTS. I decided to get rid of BT4 to make room on my hard drive, so I went into a live cd and deleted it. Now for some reason, when I boot up, all i get is the 'grub rescue' message, which i shouldnt get, because I installed Ubuntu last, so if I'm right, then the grub  that Im using is on my Ubuntu partition. I tried to reinstall grub, but now all I have when i boot up is the 'grub minimal bash-like command line' thing. That's all I can think to give you.

There are a couple of things to check
1. Is grub on the boot partition?
2. Was BT on the boot partition and you deleted it?
3. Did you run update-grub in terminal? - Was it successful?

It could be that you had the BT partition flagged as bootable and that was where your grub was installed.

If all else fails reinstall grub

---

### Post by agent_509 on 2010-07-20
> **Don1500 said:**
> There are a couple of things to check
1. Is grub on the boot partition?
2. Was BT on the boot partition and you deleted it?
3. Did you run update-grub in terminal? - Was it successful?

It could be that you had the BT partition flagged as bootable and that was where your grub was installed.

If all else fails reinstall grub

Im not sure what partition my boot was. If I go into my Ubuntu partition from a live cd, there is a grub folder with lots of files in it, so I assume I have grub installed, but that it's just not booting from there. when i try to update grub, it gives me an error saying 

```
Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) 
```

---

### Post by agent_509 on 2010-07-20
I really dont want to have to reinstall Ubuntu, is there a way to change what partition is your boot partition?

---

### Post by mike555 on 2010-07-20
To be able to boot for now you could download PLOP boot manager and burn the .iso to a cd , then use it to boot ubuntu then in ubuntu do a terminal "update-grub" ....... what I think has happened is grub is looking for the partition you deleted and panicing ...

[http://www.plop.at/en/bootmanager.html#cdinst](http://www.plop.at/en/bootmanager.html#cdinst) .... go down to #7 booting from cd

 I mean for you to just use the cd to start Ubuntu , not install anything ... the boot cd is good to have around anyway ..

---

### Post by agent_509 on 2010-07-20
oh no, this problem seems to go deeper than grub itself. I used the plop boot manager and managed to get into partition 1 (my xp partition) fine, but for some reason it wouldnt boot into my ubuntu partition.

---

### Post by agent_509 on 2010-07-20
is there any hope of recovery without completely reinstalling Ubuntu? It would be a pain to get all my old files and programs back.

---

### Post by agent_509 on 2010-07-20
what could I have done that would prevent my Ubuntu partition from booting?

---

### Post by agent_509 on 2010-07-21
bump. What should I do?

---

### Post by oldfred on 2010-07-21
Post #9 has a link to instructions on running the script. Without knowing the details on your system we are just shooting in the dark.

---

### Post by agent_509 on 2010-07-21
Im not sure how to run it though. how do you run .sh files?

---

### Post by Vaphell on 2010-07-21
dowload it to desktop
open terminal:
```

cd Desktop
sh boot_info_script055.sh

```

or
```
cd Desktop
chmod +x boot_info_script055.sh
./boot_info_script055.sh

```

---

### Post by agent_509 on 2010-07-21
ok, here are the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda5 and looks 
                       at sector 331121664 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   222,143,099   222,143,037   7 HPFS/NTFS
/dev/sda2         222,146,820   488,396,799   266,249,980   5 Extended
/dev/sda5         222,146,883   480,359,564   258,212,682  83 Linux
/dev/sda6         480,364,544   488,396,799     8,032,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FC50ACC850AC8B4A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2611fa6f-4323-4733-8902-ffa13f2c4966   ext4                                     
/dev/sda6        067e7c14-d7e1-4134-b317-bc486c17408c   swap                                     
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
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn /usepmtimer /noguiboot 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.33-02063305-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    linux    /boot/vmlinuz-2.6.33-02063305-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro   quiet splash
    initrd    /boot/initrd.img-2.6.33-02063305-generic
}
menuentry 'Ubuntu, with Linux 2.6.33-02063305-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    echo    'Loading Linux 2.6.33-02063305-generic ...'
    linux    /boot/vmlinuz-2.6.33-02063305-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.33-02063305-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 2611fa6f-4323-4733-8902-ffa13f2c4966
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set fc50acc850ac8b4a
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 164d9a2a-e329-44eb-b32e-332d3d16d789
    linux /boot/vmlinuz-2.6.30.9 root=UUID=164d9a2a-e329-44eb-b32e-332d3d16d789 ro quiet splash
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, kernel 2.6.30.9 (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 164d9a2a-e329-44eb-b32e-332d3d16d789
    linux /boot/vmlinuz-2.6.30.9 root=UUID=164d9a2a-e329-44eb-b32e-332d3d16d789 ro single
    initrd /boot/initrd.img-2.6.30.9
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 164d9a2a-e329-44eb-b32e-332d3d16d789
    linux /boot/memtest86+.bin 
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=2611fa6f-4323-4733-8902-ffa13f2c4966 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=067e7c14-d7e1-4134-b317-bc486c17408c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 133.2GB: boot/grub/core.img
 193.4GB: boot/grub/grub.cfg
 133.2GB: boot/grub/stage2
 133.2GB: boot/initrd.img-2.6.32-21-generic
 133.3GB: boot/initrd.img-2.6.32-22-generic
 133.4GB: boot/initrd.img-2.6.32-23-generic
 133.4GB: boot/initrd.img-2.6.33-02063305-generic
 133.2GB: boot/vmlinuz-2.6.32-21-generic
 133.2GB: boot/vmlinuz-2.6.32-22-generic
 133.3GB: boot/vmlinuz-2.6.32-23-generic
 133.3GB: boot/vmlinuz-2.6.33-02063305-generic
 133.4GB: initrd.img
 133.4GB: initrd.img.old
 133.3GB: vmlinuz
 133.3GB: vmlinuz.old
```

---

### Post by oldfred on 2010-07-21
Your Ubuntu install has grub2 but you still have grub legacy in the MBR. You need to reinstall grub2 to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by agent_509 on 2010-07-21
It worked!!!!!!! Thank you thank you thank you!!!!!!!!!!!!

---

### Post by oldfred on 2010-07-21
Your grub.cfg is not quite right but it may work. You still should run.

sudo update-grub


Glad you got it working.

---

