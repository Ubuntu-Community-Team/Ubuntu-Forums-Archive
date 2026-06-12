---
title: "Extreme problems booting, I see grub prompt"
date: 2009-12-08
forum: General Help
---

### Post by Jesse David on 2009-12-08
Hello,

I've recently been converted to Ubuntu from Vista (speed, programs etc... unimportant)

However, since I shut down my computer Sunday I have not been able to boot Ubuntu again.  I believe before it I received a message telling me that I needed to reboot so I believe there was an update just before I shutdown.

I should note that the way I installed Ubuntu was from the ISO in Windows, so it's actually installed as (I believe) a directory in my Windows file system.  Which has worked perfectly well until now.

My problem now is that when I try to boot into Ubuntu I get into a grub prompt screen instead of booting up into linux.  The only thing that I can do there is get a list of commands (by pressing TAB) the don't do anything, the one message I can get is 'no kernel loaded'.

I have also tried using a 'live CD' (actually USB) but I get basically the same result for some reason even though I wouldn't think that possible.  But I can still boot into Vista no problem. (Has my hardware revolted?)

I'm out of ideas (I know nothing about Grub) and I can't figure out how to do anything from windows.  Any help is appreciated.

---

### Post by Jesse David on 2009-12-09
Any ideas?  Anything that I could search for that would be able to help me from windows?

---

### Post by rvndrk3233 on 2009-12-09
YEAH, try another version.

you have to overburn, ignore size on PPC(ibook) version.It will fit AND boot.DO NOT put it on DVD, like canonocal says to.If you do, it wont ever boot the cd.

cdimages.ubuntu.com has alll versions.

9.04 works well. 9.10 has sound issues(not fixable by workaround, 9.04 has a workaround that works.)

8.10 doesn't work on PPC(ibooks), the installer disc wasn't completed, so you cant boot it.

8.04 wouldn't go below this if you want wifi support.This works ok.Would recommend 9.04 if your system can use it, though.

Windows,tssk. 

Ubuntu gets installed LAST. Windows has to have the first partition anyway.There is a grub CD if you are having issues, you can get it or I can send it to you, I HAVE the disc.

beats reformatting.

sometimes grub bootloader just gets messed up and you have to reconfigure or reinstall it. Its not too difficult to do, but you do need to read the man(ual) pages.I forget how to do it off hand.

Grub CD would be best bet to see if the bootsector or partition got wiped by accident.Windows will see linux, just ignores it.

---

### Post by zwygart on 2009-12-09
If you see the grub> line then grub is correct. Even more that you are able to boot windows.

I presume that you choose windows in the Grub menu at boot.

So here is my advice:

In the boot menu select the ubuntu entry then press "e" to edit this entry.
You will see what you should enter at the line you mention.

There is a kernel line and a initrd line. If your linux don't boot then grub didn't find the file mentioned. Newer versions of Ubuntu uses the UUID wich is the long string that you see. 

Press again on "e" on the kernel line and replace the entry UUID="blablabla" by (hdX,Y) where X is your disk (normally 0) and Y your partition (try values from 0 to 10)

Same thing with the initrd line.

To help us helping you, can you write here the lines that you see?

---

### Post by Jesse David on 2009-12-09
zwygart,
I have seen that as a fix elsewhere, but for me it's not really possible as I don't actually ever get to the grub boot menu.  Due to whatever weird way Ubuntu installs from within windows (which until now I've been perfectly OK with) I actually go through two boot menus, although it may just be something unique to me screwing with my own computer.  But like I said this was absolutely fine with Ubuntu 9.10 installed since it came out, my problem just started on Sunday.

Anyway, in the first boot menu (called Windows Boot Manager) I have the choice between Windows & Ubuntu, the second one is Grub which just gives me a command prompt instead of the grub menu.  This is what I get:

> GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions.  Anywhere else TAB lists possible device/file completions. ]

sh:grub>

Anything I try to type in there pretty much gives me an error, either saying that a command doesn't exist (most of the time), the kernel isn't loaded, or device not found.

rvndrk3233,
As for using different USB-LiveCD's I've tried 9.04 & 9.10 neither concludes in actually booting up.  Might be the USB key so I'll try formatting it and starting from scratch.  But perhaps the GRUB CD would work??

---

### Post by Leppie on 2009-12-09
try this:
```
sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk
sh:grub>initrd /boot/initrd.img-2.6.31-15-generic
sh:grub>boot
```

once booted into the system do:
```
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by Jesse David on 2009-12-09
Thanks Leppie, with your help and a look over to:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)
I was able to log into Ubuntu again.  I tried 

```
sudo grub-install /dev/sda
sudo update-grub 
```However, when I tried to reboot afterward I still had to boot up by hand again.  I'm not certain what the issue is, I'm going to try again and see if it works this time.

zwygart,
I did get to open my grub.cfg file while logged in, this is it's contents:

```

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 30ebf4a44fa59d44
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 7efcf362fcf312df
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by Jesse David on 2009-12-09
Thanks guys!!!
Well, that was a much faster reboot then the last.

I'm not 100% certain what I did to fix it but the computer seems to boot up into windows no problem now.

I did an update when I logged in last and also tried:
```
sudo grub-install /dev/sda1
sudo update-grub
```Before the update and:

```
sudo update-grub
```After.

PS In case someone reads this and tries to use Leppie's code later there's a slight typo in the fourth line:
```
sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk
sh:grub>initrd /boot/initrd.img-2.6.31-15-generic
sh:grub>boot
```(The equal sign was missing)

---

### Post by Leppie on 2009-12-10
sorry, had not noticed the typo :P

Glad you've been able to access your system in any case.
To be honest, I don't really know wubi installs (I actually do not see the point of doing wubi installs unless one does not want to free up disk space before installing, but that should not take more than a couple of minutes). What's the point of installing a stable system within a not so stable system (ntfs and fat systems have always given me headaches)?

---

### Post by Jesse David on 2009-12-10
Well, at least you gave me a direction to go in.  It took me a little while to figure out the typo since I was at first blindly just typing in your code.  Regardless my computer is working fine now.

As for the wubi install, it was convenient for me at the time.  I may eventually install from scratch but I would prefer to backup my files first which I'm a bit lazy to do.

---

