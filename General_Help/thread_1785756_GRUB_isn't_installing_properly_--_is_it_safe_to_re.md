---
title: "GRUB isn't installing properly -- is it safe to reboot?!"
date: 2011-06-18
forum: General Help
---

### Post by wilsonsamm on 2011-06-18
Hello all, I was just upgrading my system, ubuntu 10.10, and so Grub wanted to be upgraded (I thought it was a bit risky to let my system do this, but I went ahead and let it)
When trying to install it, I found kept giving some segfault messages. So I wonder if it did indeed install correctly or not.:???:

Here are the messages given to be by synaptic (or apt-get or something -- not too familiar with Ubuntu):

```
Preconfiguring packages ...
(Reading database ... 180940 files and directories currently installed.)
Preparing to replace grub-pc 1.98+20100804-5ubuntu3.3 (using .../grub-pc_1.98+20100804-5ubuntu3.3_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Setting up grub-pc (1.98+20100804-5ubuntu3.3) ...
Generating grub.cfg ...
Segmentation fault
Segmentation fault
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Segmentation fault
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Segmentation fault
Found memtest86+ image: /boot/memtest86+.bin
done

```

The window in synaptic says "Successfully applied all changes. You can close the window now." But I find it hard to tell if I can trust that or not. This is the only operating system on this computer, so if it won't boot, then I'm basically screwed. What do? Is GRUB actually installed correctly or not? Is it safe to reboot?

---

### Post by prodigy_ on 2011-06-18
Use ```
cat /boot/grub/grub.cfg
``` command in terminal to output your grub config. Look for lines starting with:
```
linux   /boot/vmlinuz-2.6.35-28-generic
initrd  /boot/initrd.img-2.6.35-28-generic
```
to see if the config was updated.

---

### Post by garvinrick4 on 2011-06-18
As long as you have a live cd or usb you can always install grub at anytime you
want and in multiple ways. This is a link below that works well for most. 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
If you ever need to install grub and are booted as you are can:
```
sudo grub-install /dev/sda
``` (sda being drive using for booting.)
at anytime you want if you ever think there is a problem. 
Grub is a very good piece of software and really have never known it to fail as long
as I install it into "mbr" of drive I am using.
```
sudo grub-mkconfig
```
Will show you the config file being made and same results as sudo update-grub

---

### Post by wilsonsamm on 2011-06-19
Ah thanks for all your help. I made sure that all the necessary stuff was in grub.cfg and dd'ed Arch Linux onto a spare USB drive I had lying around just in case. 

And rebooted. *drum roll...* Everything is in order. Thanks again. :)

---

