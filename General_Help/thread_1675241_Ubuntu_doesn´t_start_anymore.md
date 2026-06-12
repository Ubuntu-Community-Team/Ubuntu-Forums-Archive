---
title: "Ubuntu doesn´t start anymore"
date: 2011-01-25
forum: General Help
---

### Post by - Lady - on 2011-01-25
Hi,

I have this problem:
Ubuntu doesn`t mount anymore. I get only the screen where is "Ubuntu 10.04" and the dots loading above but nothing happens.
Sometimes only the cursor on the upper left blinks, and ubuntu won`t start.

I`ve tried all the options in the recovery mode but nothing worked,
also reconfigured the xorg.conf., used "startx", str-ALT-F7 , nothing helped.

Would really appreciate it, when someone could help me. 
I am a student,and have some important works/ documents saved on my desktop. :frown::icon_frown: 

Is there a chance I could get them back?

Thank you.


PS: Sorry for my bad english, I am from Germany ( at the forum there no one could advise me anything)

Lady

---

### Post by Frogs Hair on 2011-01-25
If you have a live cd , you could try to boot with that and learn what is wrong

---

### Post by - Lady - on 2011-01-25
Hi!
Thanks for your help.
How do I have to do this?
I´ve tried, but i didn´t found the recovery option.

---

### Post by Frogs Hair on 2011-01-25
See if there is any useful options  here.[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by - Lady - on 2011-01-25
Ok, I just could mount the system with the Live Cd (I chose the option start without installation). 

I  could save the important files on my usb stick.
I cannot access the mozilla folder, where the saved bookmarks are. It says :No access. You are not the owner...
 How can I pull the on my stick too?
So can I do here anything to make the system run again as it was? Or do I have to completely reinstall ubuntu?

---

### Post by - Lady - on 2011-01-25
Okay I could do the command "startx", and I get this:



(==) Logfile /var/log/Xorg.o.log, Time: ..........
(==) using config directory: /usr/lib/X11/xorg.conf.d
(EE)intel(0): [drm] failed to set drm intervace version
(EE) intel (0): Failed to become DRM master
(EE) intel (0) : failed to get resources: Bad file descriptor
(EE): intel (0): Kernel modesetting setup failed
(EE): Screen(s): found, but none have a usable configuration

Fatal server error:
no screens found

Please consult the X.Org FOundation support at.....
Please also check the log file at /var/log/Xorg.o.log for additional information

ddxSigGiveup: Closing log
giving up
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3) : Server error



Any ideas? Is it hopeless?

---

### Post by ikt on 2011-01-25
> **- Lady - said:**
> I cannot access the mozilla folder, where the saved bookmarks are. It says :No access. You are not the owner...

I can't help with the current situation, but advise:

[http://www.mozilla.com/en-US/mobile/sync/](http://www.mozilla.com/en-US/mobile/sync/)

-- You can access the mozilla folder from: Applications > accessories > terminal, then cd into the folder, and use sudo cp to copy the files.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If you have time and care enough :)

---

### Post by ppv on 2011-01-25
You could run the below command to reconfigure xserver and then run startx.

sudo dpkg-reconfigure -phigh xserver-xorg 

startx

---

### Post by Rubi1200 on 2011-01-25
Hi and welcome to the forums - Lady - :)

Two things:

1. what graphics card do you have installed?

2. when did these problems start; after an update/upgrade/hard shutdown/power failure?

Please be specific.

Finally, if you are unable to boot the Ubuntu CD, try something called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)
(includes the download link)

Once booted from the LiveCD, do the following:

Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```
Note: if sudo does not work preface the command with su instead.
This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by - Lady - on 2011-01-25
> **ikt said:**
> I can't help with the current situation, but advise:

[http://www.mozilla.com/en-US/mobile/sync/](http://www.mozilla.com/en-US/mobile/sync/)

-- You can access the mozilla folder from: Applications > accessories > terminal, then cd into the folder, and use sudo cp to copy the files.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If you have time and care enough :)

okay copy didn`t work:
bash...
refox: permission denied

---

### Post by - Lady - on 2011-01-25
> **ppv said:**
> You could run the below command to reconfigure xserver and then run startx.

sudo dpkg-reconfigure -phigh xserver-xorg 

startx

didn´t help:(

the same errors came as above

---

### Post by - Lady - on 2011-01-25
> **Rubi1200 said:**
> Hi and welcome to the forums - Lady - :)

Two things:

1. what graphics card do you have installed?

2. when did these problems start; after an update/upgrade/hard shutdown/power failure?

Please be specific.

Finally, if you are unable to boot the Ubuntu CD, try something called Slax:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)
(includes the download link)

Once booted from the LiveCD, do the following:

Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```Note: if sudo does not work preface the command with su instead.
This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


Will do this now.

Thank you **all **trying to help me!

---

### Post by - Lady - on 2011-01-25
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   300,754,943   300,752,896  83 Linux
/dev/sda2         300,756,990   312,580,095    11,823,106   5 Extended
/dev/sda5         300,756,992   312,580,095    11,823,104  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 68.7 GB, 68718428160 bytes
240 heads, 63 sectors/track, 8876 cylinders, total 134215680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,946,239     7,946,177   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0f8c54a7-6d31-4f63-a808-356c720373a4   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        afa8c92c-2bb5-4e06-8ea7-3b6a480ee090   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        48FB-33B2                              vfat       LADY                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/LADY              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
set locale_dir=($root)/boot/grub/locale
set lang=ru
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
menuentry 'Ubuntu, &#1089; Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0f8c54a7-6d31-4f63-a808-356c720373a4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, &#1089; Linux 2.6.32-27-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    echo    '&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1089;&#1103; Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0f8c54a7-6d31-4f63-a808-356c720373a4 ro single 
    echo    '&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1089;&#1103; &#1085;&#1072;&#1095;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, &#1089; Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0f8c54a7-6d31-4f63-a808-356c720373a4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, &#1089; Linux 2.6.32-26-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    echo    '&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1089;&#1103; Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0f8c54a7-6d31-4f63-a808-356c720373a4 ro single 
    echo    '&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1089;&#1103; &#1085;&#1072;&#1095;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, &#1089; Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0f8c54a7-6d31-4f63-a808-356c720373a4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, &#1089; Linux 2.6.32-25-generic (&#1088;&#1077;&#1078;&#1080;&#1084; &#1074;&#1086;&#1089;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1080;&#1103;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    echo    '&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1089;&#1103; Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0f8c54a7-6d31-4f63-a808-356c720373a4 ro single 
    echo    '&#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1089;&#1103; &#1085;&#1072;&#1095;&#1072;&#1083;&#1100;&#1085;&#1099;&#1081; ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0f8c54a7-6d31-4f63-a808-356c720373a4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=afa8c92c-2bb5-4e06-8ea7-3b6a480ee090 none            swap    sw              0       0

```
=================== sda1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  30.4GB: boot/grub/grub.cfg
  30.6GB: boot/initrd.img-2.6.32-25-generic
  30.6GB: boot/initrd.img-2.6.32-26-generic
  30.5GB: boot/initrd.img-2.6.32-27-generic
  30.4GB: boot/vmlinuz-2.6.32-25-generic
  30.4GB: boot/vmlinuz-2.6.32-26-generic
  30.4GB: boot/vmlinuz-2.6.32-27-generic
  30.5GB: initrd.img
  30.6GB: initrd.img.old
  30.4GB: vmlinuz
  30.4GB: vmlinuz.old

```

---

### Post by Rubi1200 on 2011-01-25
Quick update:

in the terminal on Slax, run this first:

```
sudo su
``` to get a root prompt

then 
```
bash ~/Desktop/boot_info_script*.sh
```

---

### Post by - Lady - on 2011-01-25
Do I have to burn the slax cd?
Cause the LiveCd works, I mean I used the option "Try without installation"

---

### Post by Rubi1200 on 2011-01-25
My apologies; I thought you could not boot with the Ubuntu CD.

Okay, let's get to the problem/solution.

Have you tried booting one of the older kernels?

Not the most recent which is 2.6.32-27, but one of the others in the menu.

What graphics card do you have installed?

---

### Post by - Lady - on 2011-01-25
> **Rubi1200 said:**
> My apologies; I thought you could not boot with the Ubuntu CD.

Okay, let's get to the problem/solution.

Have you tried booting one of the older kernels?

Not the most recent which is 2.6.32-27, but one of the others in the menu.

What graphics card do you have installed?

Yes, I tried all the options in the recovery mode, nothing helped, ubuntu just sticks on this "tty2", or "tty1" then, or it loads and loads, but in fact nothing happens.

I have this simple VGA on my laptop it´s the :"Intel® GMA 4500M HD"
My laptop is this one: [http://www.samsung.de/de/support/detail.aspx?aguid=0999caa4-58e0-41b1-8060-14b0b5bb73aa&dl=driver](http://www.samsung.de/de/support/detail.aspx?aguid=0999caa4-58e0-41b1-8060-14b0b5bb73aa&dl=driver)

---

### Post by Rubi1200 on 2011-01-25
When the computer starts and you see the entry for Ubuntu highlighted in the menu press "e" to edit.

Navigate with the arrow keys and find the line that ends with > quiet splashRemove quiet splash and type > i915.modeset=1 then "Ctrl" + "x" to boot.

Does this help?

---

### Post by - Lady - on 2011-01-25
Ok did this, but then I am in the tty1 again, when I type my login and passwort
nothing happens, then I Press ctrl-Alt-f7 and then 
there is the screen with UBUNTU 10.04 and the dots....and this goes for 15 minutes now and nothing starts..

Here I press esc and this appears:

udevd[386] can not read `/etc/udev/rules.d/99-touchpad.rules

fsck from util-linux-ng 2.17.2 
/dev/sda1: i.O.  numbersnumbersnumbers Files ...

skipping profile in /etc/apparmor/.d/disable: usr.bin.firefox


then the boot infos..
Checking battery states
Setting sensor limits.. and so on

and below all this the cursor blinks

---

### Post by Rubi1200 on 2011-01-25
Try again and when you get to tty1, after entering name and password, try this:

```
sudo service gdm stop

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg

sudo service gdm start
```

You may have to reboot

```
sudo reboot
```

---

### Post by - Lady - on 2011-01-25
> **Rubi1200 said:**
> Try again and when you get to tty1, after entering name and password, try this:

```
sudo service gdm stop


sudo dpkg-reconfigure -phigh xserver-xorg

sudo service gdm start
```You may have to reboot

```
sudo reboot
```

This time I land in the tty2


after the first command (sudo service gdm stop):
stop: Unknown instance

after "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old" 
mv: unable to run this command: "/etc/X11/xorg.conf": File does not exist (my translation)


I ran the other commands though, rebooted , but I am in the tty2 again

---

### Post by Rubi1200 on 2011-01-25
I wonder if this is the problem?

> udevd[386] can not read `/etc/udev/rules.d/99-touchpad.rules

Did you make any changes/updates to the file?

Here is a page I found in German, take a look and see if there is something that can help:
[http://wiki.ubuntuusers.de/touchpad](http://wiki.ubuntuusers.de/touchpad)

Meanwhile, I will keep looking for a solution.

(off:topic; where are you from in Germany?)

---

### Post by - Lady - on 2011-01-25
Hi!

May I post my logfile here.
It was yesterday/ 25.01.2011 at midnight, where I deinstalled the thai-fonts in Synaptic and from than on, the graphics were all down, and Ubuntu didn`t start anymore




```
Start-Date: 2011-01-24  23:26:41
Upgrade: at (3.1.11-1ubuntu5, 3.1.11-1ubuntu5.1), python-papyon (0.4.8-0ubuntu1, 0.4.8-0ubuntu2), ssh-askpass-gnome (5.3p1-3ubuntu4, 5.3p1-3ubuntu5)
End-Date: 2011-01-24  23:26:58

Start-Date: 2011-01-24  23:45:13
Purge: ttf-thai-tlwg (0.4.13-4)
End-Date: 2011-01-24  23:45:18

Start-Date: 2011-01-24  23:47:00
Remove: ubuntu-artwork (53.5), f-spot (0.6.1.5-2ubuntu7), xscreensaver-gl (5.10-3ubuntu4), openoffice.org-draw (3.2.0-7ubuntu4.1), gnome-session-canberra (0.22-1ubuntu2), python-gnome2 (2.28.0-1ubuntu1), libpurple0 (2.6.6-1ubuntu4.1), libgweather1 (2.30.0-0ubuntu1), xdg-user-dirs-gtk (0.8-1ubuntu1), ubuntu-desktop (1.197), gnome-power-manager (2.30.0-0ubuntu1), tomboy (1.2.1-0ubuntu1), python-virtkey (0.50ubuntu3), python-notify (0.1.1-2build3), libgnome-bluetooth7 (2.30.0-0ubuntu3), libmono-addins-gui0.2-cil (0.4-6), gcalctool (5.30.0.is.5.28.2-0ubuntu2), libido-0.1-0 (0.1.6-0ubuntu1), libgail18 (2.20.1-0ubuntu2), libunique-1.0-0 (1.1.6-1ubuntu2), gnome-media (2.30.0-0ubuntu1), gnome-mahjongg (2.30.0-0ubuntu6), metacity (2.30.1-0ubuntu1), nautilus (2.30.1-0ubuntu1.1), aisleriot (2.30.0-0ubuntu6), libgnome2-0 (2.30.0-0ubuntu1), mozilla-plugin-vlc (1.0.6-1ubuntu1.3), checkbox-gtk (0.9.1), update-notifier (0.99.3), evolution-indicator (0.2.8-0ubuntu1), gvfs-fuse (1.6.1-0ubuntu1build1), ubuntu-docs (10.04.3), libgtkhtml-editor0 (3.29.6.is.3.28.3-0ubuntu2), gnome-session-bin (2.30.0-0ubuntu1), gstreamer0.10-plugins-bad (0.10.18-1ubuntu1), libgtk-vnc-1.0-0 (0.3.10-2ubuntu2), openoffice.org-emailmerge (3.2.0-7ubuntu4.1), libbrasero-media0 (2.30.2-0ubuntu1), nspluginwrapper (1.2.2-0ubuntu6.10.04.1), python-ubuntuone-client (1.2.2-0ubuntu2), libgucharmap7 (2.30.0-0ubuntu1), gtk2-engines (2.20.0-0ubuntu1), system-config-printer-gnome (1.2.0+20100408-0ubuntu5.2), gnome-applets (2.30.0-0ubuntu2), libgnomecanvas2-0 (2.30.1-0ubuntu1), ubuntuone-client (1.2.2-0ubuntu2), network-manager-gnome (0.8-0ubuntu3), libevdocument2 (2.30.3-0ubuntu1.2), gnome-games-common (2.30.0-0ubuntu6), openoffice.org-impress (3.2.0-7ubuntu4.1), gucharmap (2.30.0-0ubuntu1), brltty-x11 (4.1-2ubuntu6), zenity (2.30.0-0ubuntu1), totem-plugins (2.30.2-0ubuntu1), evolution-plugins (2.28.3-0ubuntu10.2), gdebi (0.6.0ubuntu2), libpangomm-1.4-1 (2.26.2-0ubuntu1), nautilus-share (0.7.2-12build1), ubufox (0.9~rc2-0ubuntu2.1), evolution (2.28.3-0ubuntu10), libgnomeui-0 (2.24.3-1), openoffice.org-base-core (3.2.0-7ubuntu4.1), gvfs-backends (1.6.1-0ubuntu1build1), libgpod-common (0.7.93-0ubuntu1), libgtk2-perl (1.221-4ubuntu2), libgnome-window-settings1 (2.30.1-0ubuntu1), libgnomepanel2.24-cil (2.26.0-2ubuntu1), python-pygoocanvas (0.14.1-0ubuntu1), gdm-guest-session (0.15), libgtkmm-2.4-1c2a (2.20.3-0ubuntu1), gnome-disk-utility (2.30.1-1), gnome-settings-daemon (2.30.1-0ubuntu1.1), python-pyatspi (1.30.1-0ubuntu1), bleachbit (0.7.3-1), gnome-mag (0.16.1-0ubuntu1), liblaunchpad-integration1.0-cil (0.1.35), telepathy-haze (0.3.4-1), alacarte (0.13.1-0ubuntu1), ibus-gtk (1.2.0.20091215-1ubuntu4), gedit (2.30.3-0ubuntu0.1), libtelepathy-farsight0 (0.0.13-1), gnome-menus (2.30.0-0ubuntu4), gnome-system-monitor (2.28.0-1ubuntu2), libevview2 (2.30.3-0ubuntu1.2), gnome-terminal (2.30.2-0ubuntu1), gnome-session (2.30.0-0ubuntu1), libpolkit-gtk-1-0 (0.96-2ubuntu2), libgstfarsight0.10-0 (0.0.17-2ubuntu2), libwmf0.2-7-gtk (0.2.8.4-6.1ubuntu2), openoffice.org-help-en-gb (3.2.0-7ubuntu1), evolution-exchange (2.28.3-0ubuntu1), libgoocanvas3 (0.15-0ubuntu2), libindicate-gtk2 (0.3.6-0ubuntu1), python-indicate (0.3.0-0ubuntu1), transmission-gtk (1.93-0ubuntu0.10.04.1), seahorse (2.30.0-0ubuntu2), empathy (2.30.2-0ubuntu1), python-gnomecanvas (2.28.0-1ubuntu1), openoffice.org-help-en-us (3.2.0-7ubuntu1), xscreensaver-data (5.10-3ubuntu4), indicator-applet (0.3.7-0ubuntu1), python-gnomekeyring (2.30.0-0ubuntu1), libgdict-1.0-6 (2.30.0-0ubuntu1), usb-creator-gtk (0.2.22.1), python-gtksourceview2 (2.10.1-0ubuntu1), libnotify1 (0.4.5-1ubuntu4), gvfs-bin (1.6.1-0ubuntu1build1), vinagre (2.30.2-0ubuntu1), gnome-keyring (2.92.92.is.2.30.3-0ubuntu1.1), software-center (2.0.7), liblpint-bonobo0 (0.1.35), plymouth-label (0.8.2-2ubuntu2.1), libgpod4 (0.7.93-0ubuntu1), libcanberra-gtk-module (0.22-1ubuntu2), libgnome2.24-cil (2.24.1-6ubuntu1), evolution-webcal (2.28.0-1), firefox-branding (3.6.13+build3+nobinonly-0ubuntu0.10.04.1), gtk2-engines-murrine (0.90.3+git20100323-0ubuntu3), plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2.1), openoffice.org-math (3.2.0-7ubuntu4.1), libmagickcore2-extra (6.5.7.8-1ubuntu1.1), openoffice.org-writer (3.2.0-7ubuntu4.1), gstreamer0.10-plugins-good (0.10.21-1ubuntu3), m17n-db (1.5.5-1), libpango-perl (1.221-2), gnome-nettool (2.30.0-0ubuntu1), gnome-codec-install (0.4.2ubuntu2), gnome-user-guide-de (2.30.0+git20100403ubuntu2), language-selector (0.5.8), gnome-user-guide-en (2.30.0+git20100403ubuntu2), couchdb-bin (0.10.0-1ubuntu2), update-manager (0.134.11), indicator-sound (0.2.6-0ubuntu1), librsvg2-common (2.26.3-0ubuntu1), python-gmenu (2.30.0-0ubuntu4), libwnck22 (2.30.0-0ubuntu1), python-webkit (1.1.7-1), openoffice.org-gtk (3.2.0-7ubuntu4.1), gnome-utils (2.30.0-0ubuntu1), evolution-couchdb (0.4.5-0ubuntu1), gconf-editor (2.30.0-0ubuntu1), gnome-accessibility-themes (2.30.0-0ubuntu1), libindicator0 (0.3.8-0ubuntu1), notify-osd (0.9.29-0ubuntu2), gnome-user-guide-ru (2.30.0+git20100403ubuntu2), libcryptui0 (2.30.0-0ubuntu2), libgdu-gtk0 (2.30.1-1), simple-scan (1.0.3-0ubuntu1), libgtkspell0 (2.0.16-1), libgail-gnome-module (1.20.1-2), firefox (3.6.13+build3+nobinonly-0ubuntu0.10.04.1), libclutter-gtk-0.10-0 (0.10.4-0ubuntu1), python-desktopcouch (0.6.4-0ubuntu3.1), libaccess-bridge-java-jni (1.26.2-3), python-glade2 (2.17.0-0ubuntu2), telepathy-butterfly (0.5.11-0ubuntu1), gnome-about (2.30.2-0ubuntu1), libgcr0 (2.92.92.is.2.30.3-0ubuntu1.1), libgnome-desktop-2-17 (2.30.2-0ubuntu1), gnome-system-tools (2.30.0-0ubuntu3), libedataserverui1.2-8 (2.28.3.1-0ubuntu5), eog (2.30.0-0ubuntu1), gdm (2.30.2.is.2.30.0-0ubuntu4), libgraphviz4 (2.20.2-8ubuntu3), screensaver-default-images (0.2-1), mozplugger (1.13.3-1ubuntu1), python-launchpad-integration (0.1.35), libavahi-ui0 (0.6.25-1ubuntu6.1), python-uno (3.2.0-7ubuntu4.1), libpanel-applet2-0 (2.30.2-0ubuntu0.2), gnome-themes-selected (2.30.0-0ubuntu1), libgtkhtml3.14-19 (3.29.6.is.3.28.3-0ubuntu2), python-vte (0.23.5-0ubuntu1.1), libvte9 (0.23.5-0ubuntu1.1), gnome-bluetooth (2.30.0-0ubuntu3), gnome-user-share (2.30.0-0ubuntu2), xulrunner-1.9.2 (1.9.2.13+build3+nobinonly-0ubuntu0.10.04.1), indicator-applet-session (0.3.7-0ubuntu1), libdbusmenu-gtk1 (0.2.9-0ubuntu3.1), libglade2.0-cil (2.12.9-4), at-spi (1.30.1-0ubuntu1), software-properties-gtk (0.75.10.1), tsclient (0.150-3ubuntu1), libclutter-1.0-0 (1.2.4-0ubuntu1), compiz-gnome (0.8.4-0ubuntu15), libgnome2-canvas-perl (1.002-2build1), libubuntuone-1.0-1 (0.3.1-0ubuntu1), libexchange-storage1.2-3 (2.28.3.1-0ubuntu5), mousetweaks (2.30.0-0ubuntu1), gnome-themes-ubuntu (0.6.1), sun-java6-plugin (6.22-0ubuntu1~10.04), libpoppler-glib4 (0.12.4-0ubuntu5.1), libglade2-0 (2.6.4-1build1), evince (2.30.3-0ubuntu1.2), policykit-1-gnome (0.96-2ubuntu2), libcanberra-gtk0 (0.22-1ubuntu2), libgnomekbd4 (2.30.2-0ubuntu0.1), flashplugin-installer (10.1.102.65ubuntu0.10.04.1), apturl (0.4.1ubuntu4), python-aptdaemon-gtk (0.11+bzr345-0ubuntu4.1), ibus-m17n (1.2.0.20091217-1), libgail-common (2.20.1-0ubuntu2), python-desktopcouch-records (0.6.4-0ubuntu3.1), ubuntu-mono (0.0.18), python-appindicator (0.0.19-0ubuntu4), libgnome-media0 (2.30.0-0ubuntu1), libgtk2-gladexml-perl (1.007-1), python-gtkspell (2.25.3-4.1ubuntu4), network-manager-pptp-gnome (0.8-0ubuntu3), nautilus-sendto (2.28.4-0ubuntu1), gstreamer0.10-x (0.10.28-1), compiz-plugins (0.8.4-0ubuntu15), vlc (1.0.6-1ubuntu1.3), desktopcouch (0.6.4-0ubuntu3.1), libappindicator0 (0.0.19-0ubuntu4), yelp (2.30.0-0ubuntu2), libm17n-0 (1.5.5-1), openoffice.org-help-de (3.2.0-7ubuntu1), synaptic (0.63.1ubuntu7), m17n-contrib (1.1.10-1), libwebkit-1.0-2 (1.2.5-0ubuntu0.10.04.1), indicator-session (0.2.8-0ubuntu2), gksu (2.0.2-2ubuntu2), gtk2-engines-pixbuf (2.20.1-0ubuntu2), gnome-screensaver (2.30.0-0ubuntu2), ibus (1.2.0.20091215-1ubuntu4), openoffice.org-calc (3.2.0-7ubuntu4.1), plymouth-x11 (0.8.2-2ubuntu2.1), openoffice.org-help-ru (3.2.0-7ubuntu1), libnautilus-extension1 (2.30.1-0ubuntu1.1), librsvg2-2 (2.26.3-0ubuntu1), libbonoboui2-0 (2.24.3-0ubuntu1), ibus-table (1.2.0.20100111-1), onboard (0.93.0-0ubuntu4), libgksu2-0 (2.0.13~pre1-1ubuntu4.1), quadrapassel (2.30.0-0ubuntu6), libgnome2-perl (1.042-2build1), jockey-gtk (0.5.8-0ubuntu8.1), pitivi (0.13.4-0ubuntu3), libatspi1.0-0 (1.30.1-0ubuntu1), python-gnomeapplet (2.30.0-0ubuntu1), python-farsight (0.0.17-2ubuntu2), gnome-control-center (2.30.1-0ubuntu1), liblaunchpad-integration1 (0.1.35), python-papyon (0.4.8-0ubuntu2), libgtksourceview2.0-0 (2.10.4-0ubuntu1), evolution-data-server (2.28.3.1-0ubuntu5), gnome-user-guide (2.30.0+git20100403ubuntu2), libpango1.0-0 (1.28.0-0ubuntu2.1), python-wnck (2.30.0-0ubuntu1), flashplugin-nonfree (10.1.102.65ubuntu0.10.04.1), brasero (2.30.2-0ubuntu1), gtkorphan (0.4.4-1), compiz (0.8.4-0ubuntu15), gvfs (1.6.1-0ubuntu1build1), ubuntuone-client-gnome (1.2.2-0ubuntu2), gnome-panel (2.30.2-0ubuntu0.2), compiz-fusion-plugins-main (0.8.4-0ubuntu3), ssh-askpass-gnome (5.3p1-3ubuntu5), libgtk2.0-bin (2.20.1-0ubuntu2), libgtk2.0-cil (2.12.9-4), totem (2.30.2-0ubuntu1), libmetacity-private0 (2.30.1-0ubuntu1), totem-mozilla (2.30.2-0ubuntu1), python-ibus (1.2.0.20091215-1ubuntu4), openoffice.org-gnome (3.2.0-7ubuntu4.1), apport-gtk (1.13.3-0ubuntu2), openjdk-6-jre (6b20-1.9.2-0ubuntu1~10.04.1), icedtea6-plugin (6b20-1.9.2-0ubuntu1~10.04.1), libgnome-pilot2 (2.0.17-0ubuntu5), gnome-icon-theme (2.28.0-1ubuntu1), indicator-application (0.0.19-0ubuntu4), humanity-icon-theme (0.5.2.1), python-gtk2 (2.17.0-0ubuntu2), light-themes (0.1.6.6), openoffice.org-core (3.2.0-7ubuntu4.1), firefox-gnome-support (3.6.13+build3+nobinonly-0ubuntu0.10.04.1), libgtk2.0-0 (2.20.1-0ubuntu2), nautilus-sendto-empathy (2.30.2-0ubuntu1), file-roller (2.30.1.1-0ubuntu2), python-ubuntuone (0.3.1-0ubuntu1), gnomine (2.30.0-0ubuntu6)
Purge: libthai-data (0.1.13-1build1), libthai0 (0.1.13-1build1)
End-Date: 2011-01-24  23:53:36

Start-Date: 2011-01-25  00:39:00
Remove: openoffice.org-l10n-de (3.2.0-7ubuntu1), menu (2.1.43ubuntu1), libaccess-bridge-java (1.26.2-3), openoffice.org-l10n-ru (3.2.0-7ubuntu1), libflite1 (1.3-release-2build1), odbcinst1debian1 (2.2.11-21), openoffice.org-l10n-en-gb (3.2.0-7ubuntu1), libdca0 (0.0.5-3), m4 (1.4.13-3), java-common (0.34), icedtea-6-jre-cacao (6b20-1.9.2-0ubuntu1~10.04.1), libiso9660-7 (0.81-4), libcddb2 (1.3.2-0ubuntu1), libfftw3-3 (3.2.2-1), libass4 (0.9.9-0ubuntu1), odbcinst (2.2.11-21), sun-java6-bin (6.22-0ubuntu1~10.04), openjdk-6-jre-lib (6b20-1.9.2-0ubuntu1~10.04.1), libdvbpsi5 (0.1.6-1), unixodbc (2.2.11-21), openjdk-6-jre-headless (6b20-1.9.2-0ubuntu1~10.04.1), libvlc2 (1.0.6-1ubuntu1.3), libsdl-image1.2 (1.2.10-1), sun-java6-jre (6.22-0ubuntu1~10.04), libenca0 (1.12-1), vlc-nox (1.0.6-1ubuntu1.3), libupnp3 (1.6.6-4), deborphan (1.7.28ubuntu1), libmatroska0 (0.8.1-1.1), tzdata-java (2010o-0ubuntu0.10.04), libgme0 (0.5.5-1), freepats (20060219-1), libiptcdata0 (1.0.3-1ubuntu1), libxcb-keysyms1 (0.3.6-1build1), libwildmidi0 (0.2.2-2), liborc-0.4-0 (0.4.3-5), libdc1394-22 (2.1.2-2), libkate1 (0.3.7-3), libcdaudio1 (0.99.12p2-9), libmimic0 (1.0.4-2build1), liblua5.1-0 (5.1.4-5), libsoundtouch1c2 (1.3.1-2), ca-certificates-java (20100406ubuntu1), vlc-data (1.0.6-1ubuntu1.3), libtar (1.2.11-6), libcelt0-0 (0.7.1-1), libvlccore2 (1.0.6-1ubuntu1.3), libvcdinfo0 (0.7.23-4ubuntu2), libebml0 (0.7.7-3.1), libofa0 (0.9.3-3.1), libmms0 (0.4-2), vlc-plugin-pulse (1.0.6-1ubuntu1.3)
End-Date: 2011-01-25  00:39:43

```









I am from Freilassing (Bavaria) ^^

---

### Post by - Lady - on 2011-01-25
This is really strange I never removed all the packages, only two with ThaiFonts
Maybe I can install the packages after the "remove" again somehow and then run the xorg-reconfig?
What do you thinK? And how I have to install them again?

---

### Post by Rubi1200 on 2011-01-25
Hi,
okay I just looked at the logs a bit more carefully and it does not look good.

Whatever happened all kinds of essential packages were removed!

If you saved your data it might be better to just reinstall and make a fresh start.

If you had just removed one or two packages we might have been able to do something, but in this situation?

As far as the .mozilla files are concerned, give me a few minutes and I will help you save that stuff.

---

### Post by - Lady - on 2011-01-25
Dear Rubi1200

I really appreciate your help and patience.
Everything works now. I did this:

tty2-> sudo apt-get install ubuntu-desktop--------not helped couldn`t connect.

Then Recovery mode, netroot--turned on WLAN, same command ----------didn´t work

Then in netroot inserted the dsl-cable and run the command, then sudo apt-get update.
updates are loading at least

Then in about 10 minutes everything starts as nothing ever happened.

Ok while reboot the screens were not that usual , but at least i have back my gnome, and all the data on the desktop and the bookmarks.

I just wanted to clean Ubuntu, there are so many packages that I don´t need, and the updates came all the time for the unneed one. So I will look up other distributions maybe, or choose a minimal installation..

But again REALLY Thank you very much!!!

Greetz,

Lady

---

### Post by Rubi1200 on 2011-01-25
Great news!

I am really glad you got things sorted out and working again.

You are more than welcome too for the help :)

---

