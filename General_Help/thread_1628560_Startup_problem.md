---
title: "Startup problem"
date: 2010-11-22
forum: General Help
---

### Post by MiantCub on 2010-11-22
[FONT=Arial Black]OK, I'm updating my system, and I restart it right afterward, then when I bring it back up, and I choose which operating system, naturally, I chose Ubuntu, but then it restarts itself, then I try again, hoping it was just a minor glitch, but it still restarts.  Any advice would be appreciated.[/FONT]

---

### Post by dcstar on 2010-11-23
> **MiantCub said:**
> OK, I'm updating my system, and I restart it right afterward, then when I bring it back up, and I choose which operating system, naturally, I chose Ubuntu, but then it restarts itself, then I try again, hoping it was just a minor glitch, but it still restarts.  Any advice would be appreciated.

[LIST=1]
[*]Please do not use weird fonts.
[*]Select the previous kernel in the Grub list.
[/LIST]

---

### Post by MiantCub on 2010-11-24
[FONT=Arial]Usually when I hit "Ubuntu", a list of Ubuntus would come up and I would pick the top one, but now, no list comes up, and a message saying that it can't find a certain file comes up, but only in a flash.  The only thing that comes up is WIndows and Ubuntu, and when I chose "Ubuntu", after the flash, it circles back to the beginning.
[/FONT]

---

### Post by sikander3786 on 2010-11-24
> **MiantCub said:**
> [FONT=Arial]Usually when I hit "Ubuntu", a list of Ubuntus would come up and I would pick the top one, but now, no list comes up, and a message saying that it can't find a certain file comes up, but only in a flash.  The only thing that comes up is WIndows and Ubuntu, and when I chose "Ubuntu", after the flash, it circles back to the beginning.
[/FONT]
You can post in the default font and make it easy for us to read your posts :-)

I feel this is a Wubi install. Is Ubuntu installed inside Windows using the wubi.exe program?

---

### Post by bcbc on 2010-11-24
+1 on what Sikander said

There has been a grub update that is wreaking havoc with wubi installs.

If it's a 10.04 install, the fix is to boot an Ubuntu live cd, loop mount the wubi root.disk and manually edit the grub.cfg.

If it's a 10.04 to 10.10 upgrade, copy the c:\ubuntu\winboot\wubildr file over the c:\wubildr file.


To edit grub.cfg:
Boot a live CD, identify your windows partition that contains the root.disk (this example assumes /dev/sd**a1**), and then edit grub.cfg as follows:
```
sudo mkdir /media/win 
sudo mount /dev/sd**a1** /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

Delete all lines up to (not including) the first line that starts with "menuentry"
Save, reboot.

If all that is 'too much'. Just use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk. 

PS this assumes that your problem is due to the recent grub update. If you did something strange, or had to do a hard shutdown in Ubuntu recently, you might need some other fix.

---

### Post by MiantCub on 2010-11-24
> **sikander3786 said:**
> You can post in the default font and make it easy for us to read your posts :-)

I feel this is a Wubi install. Is Ubuntu installed inside Windows using the wubi.exe program?

[FONT=Verdana]Yes, it is.

[/FONT]> **sikander3786 said:**
> Ubuntu will kill Microsoft..... Some day.....

I can sympathize with your enthusiasm.  Only trouble is too many dummies get what they pay for ... SCREWED!!!

---

### Post by MiantCub on 2010-11-24
> **bcbc said:**
> +1 on what Sikander said

There has been a grub update that is wreaking havoc with wubi installs.

If it's a 10.04 install, the fix is to boot an Ubuntu live cd, loop mount the wubi root.disk and manually edit the grub.cfg.

If it's a 10.04 to 10.10 upgrade, copy the c:\ubuntu\winboot\wubildr file over the c:\wubildr file.


To edit grub.cfg:
Boot a live CD, identify your windows partition that contains the root.disk (this example assumes /dev/sd**a1**), and then edit grub.cfg as follows:
```
sudo mkdir /media/win 
sudo mount /dev/sd**a1** /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```Delete all lines up to (not including) the first line that starts with "menuentry"
Save, reboot.

If all that is 'too much'. Just use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk. 

PS this assumes that your problem is due to the recent grub update. If you did something strange, or had to do a hard shutdown in Ubuntu recently, you might need some other fix.

OK, thanks a bunch for the advice.  I'll try booting from a CD.
The problem occurred when I restarted right after I did the update, so yeah, I figure that the problem is due to the grub update.

---

### Post by The Squirrel Unit on 2010-11-26
> **bcbc said:**
>  loop mount the wubi root.disk 

Same issue...updated grub/kernel this morning (10.04 wubi) and get the grub prompt.  What exactly do you mean by "loop mount" the wubi root.disk?  I get that I need to manually edit the grub.cfg file. 

I'm fairly new to ubuntu so please forgive my ignorance.

Thanks,
         TSU

---

### Post by bcbc on 2010-11-26
> **The Squirrel Unit said:**
> Same issue...updated grub/kernel this morning (10.04 wubi) and get the grub prompt.  What exactly do you mean by "loop mount" the wubi root.disk?  I get that I need to manually edit the grub.cfg file. 

I'm fairly new to ubuntu so please forgive my ignorance.

Thanks,
         TSU
Since wubi installs Ubuntu to a virtual disk (the file root.disk) it needs to be mounted with the loop option (it simulates the file as a block device, like a partition). [http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)

The grub.cfg file in question is a file within the root.disk so you can't access it until the root.disk is loop mounted.

So, from a live CD we need to mount the windows partition that contains root.disk to access that.
Then we loop mount the root.disk to access the virtual disk.
Then we can access and edit the grub.cfg.

---

### Post by colmeweb on 2010-11-30
@bcbc

I have been trying to follow the instructions from reply #5 but my file looks like this

```
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
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
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" 

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```Could you please help me figure out which lines to delete? There are quite a few "menuentry" lines.

Thanks

---

### Post by bcbc on 2010-11-30
Just like this:
```
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  splash vga=786  quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 5a4ca2994ca26f85
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single  splash vga=786
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" 

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

Please note this is a temporary fix. If you install/uninstall a kernel it will regenerate this file. 

Once you have completed this workaround to get it booting, you can apply [this permanent fix]("http://ubuntuforums.org/showpost.php?p=10180520&postcount=78"). (But you need to first do the above to boot wubi before doing the second fix).

---

### Post by colmeweb on 2010-11-30
Thank you so much :)

I am back with my Lucid, and seriousl thinking about reinstalling without the wubi.

---

### Post by skycor on 2010-12-06
Thanks for posting that fix! It worked beautifully!

---

### Post by MiantCub on 2010-12-15
How do I loop mount root.disk?

---

### Post by bcbc on 2010-12-15
*Rubi1200* has created a [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") that explains all this and how to solve the problem you are experiencing. Please have a read of that thread, and if you need any help you can post back either here or in that thread.

The quick answer to your question is: you will have to boot from an Ubuntu CD/USB, select "Try without installing" (often referred to as Live CD). Then identify and mount the ntfs partition that contains the root.disk. Then you specify the loop option when you mount the root.disk  (sudo mount **-o loop** /<path-to-root.disk>/root.disk /mnt)

But read that thread it shows step by step what you need to do.

---

### Post by mohave on 2010-12-19
I had lost all my ubuntu lucid bacause of a kernel upgrade.
Thanks a lot bcbc !!!

---

