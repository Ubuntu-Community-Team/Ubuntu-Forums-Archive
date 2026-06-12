---
title: "Wubi Booting Problems"
date: 2011-05-16
forum: General Help
---

### Post by poker158149 on 2011-05-16
Hi everyone.

Alright, I've had Wubi running on my Windows 7 PC for a few months now and it's great. I had given Wubi 5GB of space when I installed. After using it for some time, I decided I wanted some more space for my Wubi install. I looked up how to do it and came across a few options. The one I chose is this one:

"Download [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), open a terminal and run: 

```
sudo sh wubi-add-virtual-disk /home 15000
```Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.  
You  should now reboot. If you are happy with the result, you can now remove  /home.backup. To undo the changes remove /home, copy rename  /home.backup to /home and remove the /home line in /etc/fstab."

Well, I did this exactly how it says. I mean, come on, it's three steps. The only problem - after I rebooted, I could not boot into Wubi. It has an error when I try, but it goes away too quickly for me to read, then it just restarts my computer. 

How can I fix this without having to reinstall Wubi completely?
I'm willing to reinstall if it's the absolute only option, but I'm willing to try anything to get it working again.

Oh, and I found another way to change the space, so no worries about that. I just have to get back into Wubi to do it...

---

### Post by Rubi1200 on 2011-05-16
Hi,

please do the following so we can help you troubleshoot and fix this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

new script ( if you have 11.04)
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

---

### Post by poker158149 on 2011-05-16
Hi.

The problem is that I can't boot into Ubuntu at all. And this is Wubi, so I have no CD. It's downloaded and installed like any other program. 

When I try to boot into Ubuntu it flashes this for a split-second then my computer restarts:

```

Try (h0,0): No wubildr
Try (h0,1): No wubildr
Try (h0,2):
```Now, since it only flashes for a second that may be slightly off, but I'm pretty sure that's it.

EDIT: I'm downloading Ubuntu now to make a Live CD out of it, then I'll post the boot info script results here.

---

### Post by Rubi1200 on 2011-05-16
The message you are seeing is grub4dos (which Wubi uses to boot) searching the partitions to find the wubildr file it needs to start the process.

In this situation, I think the best thing to do is download and burn to CD the Ubuntu image so you can post the results of the script.

It is always a good idea to have an Ubuntu CD handy for recovery purposes and in this case we will likely need it to fix this for you.

I will keep an eye on the thread and try and help later when you post the results.

Good luck :-)

---

### Post by poker158149 on 2011-05-16
Thank you for helping out.

But, does it matter which version of Ubuntu I download to make the CD out of? There's 11.04, the new one; or 10.04, the same version as Wubi I'm using.

---

### Post by poker158149 on 2011-05-16
And here are those results!

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/home.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,142,335    16,140,288  27 Hidden HPFS/NTFS
/dev/sda2    *     16,142,336    16,347,135       204,800   7 HPFS/NTFS
/dev/sda3          16,347,136   976,771,119   960,423,984   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       de9d2a88-0179-4162-b275-7645a20b05c4   ext4                                     
/dev/sda1        AA2EBDC22EBD8839                       ntfs       Recovery                      
/dev/sda2        E2267A58267A2DA3                       ntfs       System Reserved               
/dev/sda3        CC787BAB787B92C6                       ntfs       Windows                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EC18515E1851293A                       ntfs       FreeAgent Drive               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set cc787bab787b92c6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set cc787bab787b92c6
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-31-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-31-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, Linux 2.6.32-31-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-31-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, Linux 2.6.32-30-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-30-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-30-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set cc787bab787b92c6
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set aa2ebdc22ebd8839
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e2267a58267a2da3
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

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
/host/ubuntu/disks/home.disk    /home    ext3    loop    0    0

================= sda3/Wubi: Location of files loaded by Grub: =================


   7.2GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.32-24-generic
   1.0GB: boot/initrd.img-2.6.32-27-generic
   2.0GB: boot/initrd.img-2.6.32-30-generic
   1.0GB: boot/initrd.img-2.6.32-31-generic
   3.2GB: boot/vmlinuz-2.6.32-24-generic
    .7GB: boot/vmlinuz-2.6.32-27-generic
   3.4GB: boot/vmlinuz-2.6.32-30-generic
   3.6GB: boot/vmlinuz-2.6.32-31-generic
   1.0GB: initrd.img
   2.0GB: initrd.img.old
   3.6GB: vmlinuz
   3.4GB: vmlinuz.old

```

---

### Post by Rubi1200 on 2011-05-16
Thanks for posting the results.

Okay, so the problem is probably this:
> loopback loop0 /ubuntu/disks/root.disk
In general, whenever this appears in the grub.cfg before the first menuentry you will have a problem.

The solution is in the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem # 2, solution # 1.

You need to do this from the LiveCD of course.

Once you are back in Ubuntu, apply the Permanent Fix also explained in the thread.

If you encounter any problems, let me know please.

---

### Post by poker158149 on 2011-05-16
Well, I've read it and I'm pretty sure I'm capable, but there's one problem. 

This is how I'm supposed to do it:

"Boot an Ubuntu LiveCD/USB, loop  mount the wubi root.disk and manually edit the grub.cfg file."

Well, how do I do that? When I boot my CD it just brings me to the "Test Ubuntu/Install Ubuntu" screen. How do I mount the root.disk and where do I find the grub.cfg after I mount the root.disk? Do I have to actually start running Ubuntu?

------------------------

EDIT:: I have the root.disk mounted and I think I found the grub.cfg file (there are multiple). I'm just not sure what to edit. The code that they give you in the solution is not in the grub.cfg file. Maybe it's not supposed to be there and I'm misreading it, or maybe I'm editing the wrong grub.cfg.

EDIT 2:: I think I'm misreading it. Those are commands I'm supposed to be running. (lightbulb went on). I'll try it and let you know what happened.

FINAL EDIT:: I got it! It's all fixed and working again. Thanks so much for your patience and help!

---

### Post by Rubi1200 on 2011-05-17
Excellent! I am pleased you got it sorted out :-)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

