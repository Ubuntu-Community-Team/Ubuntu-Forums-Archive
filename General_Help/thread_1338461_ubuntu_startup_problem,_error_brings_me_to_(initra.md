---
title: "ubuntu startup problem, error brings me to (initramfs) prompt"
date: 2009-11-26
forum: General Help
---

### Post by l0ijoat on 2009-11-26
Hi, I'm having a problem that started last night when my computer froze and I tried to restart it. Ubuntu now doesn't start...it just shows some error messages that end with an (initramfs) prompt. I have no idea what to do, I'm using ubuntu 9.04. I couldn't see all the error message cause it gets pushed up the screen, but I copied down what I could, hope it gives you a clue as to what the problem could be. Thanks in advance!
hart
```

Boot from (hd0,5) ext3   f7d4adb4-5e5f-4df9-9e4c-095915f1dab2
Starting up ...
Loading, please wait...
usplash: Setting mode 1152x864 failed
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/2f2e3de1-a798-4039-9253-dddb3e760934) = dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/2f2e3de1-a798-4039-9253-dddb3e760934
kinit: No resume image, doing normal boot...
usplash: Using mode 1024x768
mount: mounting /dev/disk/by-uuid/f7d4adb4-5e5f-4df9-9e4c-095915f1dab2 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

---

### Post by jamlam on 2009-11-26
I'm also getting this problem after today's updates. Boot fails with a blank screen, if I boot into single user mode I can see the same errors as mentioned above. I've tried mounting the disk manually and get an error "Block to replay outside the filesystem"

---

### Post by drs305 on 2009-11-26
It looks like grub may not be pointing to the correct partition. Check the /boot/grub/menu.lst entries - the UUIDs may not be correct. l0ijoat, is your system installed on sda5?

At the menu, press "e" and take a look at the UUID. If you aren't sure if it's correct or see it isn't, you can change the UUID to "/dev/sdXY" with XY being the device and partition numbers (sda1, sdb5, etc). 
If you can get to a command prompt, you can check the UUIDs with:
```

sudo blkid

```

---

### Post by l0ijoat on 2009-11-26
drs305,
I'm really not sure how to do anything right now. like i said, i'm stuck at this (initramfs) prompt and i can't figure out how to get to any menu or a command prompt, any ideas?
hart

---

### Post by drs305 on 2009-11-26
> **l0ijoat said:**
> drs305,
I'm really not sure how to do anything right now. like i said, i'm stuck at this (initramfs) prompt and i can't figure out how to get to any menu or a command prompt, any ideas?
hart

You would reboot. You can issue the "reboot" or "sudo reboot" from that prompt (or power off, although that is not the best solution). Get back to the Grub boot menu. Hit ESC to pause the menu, then pick up where I started describing how to edit the menu.

---

### Post by l0ijoat on 2009-11-26
ok, thanks for being patient, i'm slow with this stuff! i got to that menu. it says
uuid    f7d4adb4-5e5f-4df9-9e4c-095915f1dab2. i'm not sure what partition ubuntu is installed on - is there a way i can find out? i'm running it on a laptop where windows was installed first and i still have that partition as well. also, i'm not sure how to change the UUID from that editing menu
hart

---

### Post by l0ijoat on 2009-11-26
actually i figured out how to edit it, but I just need to figure what partition it should be i guess...?
hart

---

### Post by drs305 on 2009-11-26
> **l0ijoat said:**
> actually i figured out how to edit it, but I just need to figure what partition it should be i guess...?
hart

If this is a single drive with a Windows partition, and on which you then installed Ubuntu, it is most likely **/dev/sda5**

You can run "find /boot/grub/stage1". Remember that if it responds with (hd0,0), that would be /dev/sda1, (hd0,4) would be /dev/sda5, etc.

If you still can't get into your system, this is an old but classic post on restoring Grub:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by l0ijoat on 2009-11-26
drs305,
i think it's (hd0,5) - so then it would be /dev/sda6 - i tried that and it just says "error 15: file not found". i'll see if that thread helps, thanks for your help thus far!
hart

---

### Post by l0ijoat on 2009-11-27
alright, so i've tried with the live cd - and "reinstalling" grub was successful i think, but it didn't make a difference. also i realized that when i booted using the live cd and tried to mount my old ubuntu partition it wouldn't work. it came up with an error:
"error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda6, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so"
however when i mount my old windows partition while using the live cd it works....what do you think this means?
hart

---

### Post by l0ijoat on 2009-11-27
seem to have fixed it! all i had to do was ```
sudo fsck /dev/sda6
```
seems to be running smoothly again
hart

---

### Post by illuniel on 2010-10-23
i know that this is an old thread, but would that solution apply to 10.04 and 10.10 as well? 

i am currently working on 8 desktops and at least 2 have that error after they've run for a day or two..

---

