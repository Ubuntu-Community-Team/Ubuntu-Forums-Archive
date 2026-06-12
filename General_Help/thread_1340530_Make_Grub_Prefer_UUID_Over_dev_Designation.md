---
title: "Make Grub Prefer UUID Over /dev Designation"
date: 2009-11-28
forum: General Help
---

### Post by jamesisin on 2009-11-28
I am having a boot problem when I add more SATA drives to my system.  It appears that telling Grub to use UUID's will fix this problem (fstab is already using them).  You can read the full thread here:

[http://ubuntuforums.org/showthread.php?t=1337044](http://ubuntuforums.org/showthread.php?t=1337044)

Can someone walk me through the necessary steps to point Grub at the UUID('s) instead of the /dev path(s)?

(The system is running 9.10 desktop.)

---

### Post by jamesisin on 2009-11-29
Anybody?  I'd really like to get this machine up and running--with all its drives.

---

### Post by Leppie on 2009-11-29
By default GRUB2 refers to partitions with the uuid.

What does your grub.cfg look like?

---

### Post by jamesisin on 2009-11-29
Here is the pertinent section:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
```

---

### Post by Leppie on 2009-11-29
Waht is the output of the command
```
$ls -l /dev/disk/by-uuid
```

---

### Post by jamesisin on 2009-11-29
```
total 0
lrwxrwxrwx 1 root root 10 2009-11-28 11:00 5e0c996c-676c-45a5-87ff-3f78eb157646 -> ../../sdc5
lrwxrwxrwx 1 root root  9 2009-11-28 11:03 77ce1011-021f-4c31-847a-743c15ce6e25 -> ../../md0
lrwxrwxrwx 1 root root 10 2009-11-28 11:00 b8c9f44c-af18-4bfc-919a-5941628aa25b -> ../../sdc1

```

---

### Post by Leppie on 2009-11-29
Well, you could try to change the piece
```
root=/dev/sdc1
```

to
```
root=UUID=b8c9f44c-af18-4bfc-919a-5941628aa25b
```

for one of your entries and see if it boots correctly selecting that entry at boot. if it does, you can modify all entries likewise.

---

### Post by jamesisin on 2009-11-29
This was actually discussed in the other thread.  It looks like this file is auto-generated from other sources.  There must be a preferred method for making changes like this to Grub.  I don't understand why this system is not using UUID's if Grub2 uses them.  I would even consider reinstalling Grub if that were the preferred route.  I just don't know what the best practice would be in this case.

---

### Post by Leppie on 2009-11-29
Try to rename the grub.cfg (to something like grub.cfg.old) and run these commands:
```
$sudo grub-install --recheck /dev/sdc  ##change /dev/sdc to your boot device.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sdc
$sudo update-grub  ##this will recreate your grub.cfg
```

check if the entries now are using uuid references.

---

### Post by shaggy999 on 2009-11-29
In addition to the suggestion above, if that doesn't work I mentioned in the other thread about a line that needed to be commented out. You might try uncommenting it and change true to false to explicitly state that UUIDs must be used.

---

### Post by shaggy999 on 2009-11-29
I just found this, which may help as well. It has to do with what your original problem was (PATA vs SATA):

[http://www.robotsystematic.com/2009/ubuntu/reminder-to-self-grub2-karmic-harddrive-fix-when-using-pata-sata/](http://www.robotsystematic.com/2009/ubuntu/reminder-to-self-grub2-karmic-harddrive-fix-when-using-pata-sata/)

The article doesn't mention it, but you may have to run update-grub after making those changes.

---

### Post by jamesisin on 2009-11-29
Shaggy - I figured I'd give yours a shot first since it was so simple.  Here is the output:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
done

```

Doing so made no apparent changes to grub.cfg:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
```

I am going to try Leppie's solution.

(I may come back to that article later.)

---

### Post by shaggy999 on 2009-11-29
The article I posted actually has to do with changing device.map so possibly my suggestion + changing device.map might be your way to go. Based on the errors reported it's quite possible that the reason why it's using /dev/sdX instead of UUID's is because when it tries to calculate UUIDs they don't match the device.map file so it falls back to using /dev/sdX as a backup. Just a thought.

---

### Post by shaggy999 on 2009-11-29
In the end, a temporary solution that is guaranteed to work is to change the /dev/sdX references to UUIDs in the /boot/grub/grub.cfg file, but they will be overwritten the next time 'update-grub' is executed so you have to be very careful when you install or upgrade packages.

---

### Post by jamesisin on 2009-11-29
Well, Leppie wins the gold star on this one.  Shaggy, you get runner-up.

These two commands did the job:

```
sudo grub-install --recheck /dev/sdc
sudo update-grub
```

Thanks, everybody.

---

### Post by Leppie on 2009-11-29
Glad it worked :D

---

### Post by calmera on 2009-12-04
Eureka!

I just wanted to pull out an old drive, but got stuck in front of the computer for 5 hours. Thanks to this thread I could finally go to sleep. Thanks guys.

I had 3 IDE/PATA drives up and running with 8.04 server. Then I added 2 SATA drives and installed 9.04 on the first.
All is ok. Then I pulled out the first IDE drive containing 8.04 and whops, black screen. No grub loading. When I hit the powerbutton I got busybox and initramfs saying it cant mount root system.
I tried all the guides on recovering grub, reinstalling grub, chroot`ing etc.
I had to do the unthinkable of editing grub.cfg. It was stuck on /dev/sdd1 when it should be /dev/sdc1.
Then, it booted, but it took ages for grub to load and then ages to boot.
The grub-install with the root-driectory param did`nt solve anything and grub-update gave me the cant find drive error.

Then I ran Leppis commands, and this time no errors.
Updated fstab with UUUID`s, rearanged drives in BIOS and I cut down boot time with 40 seconds. Grub loads in about 2.

Thanks again!

---

### Post by jamesisin on 2009-12-04
Excellent.  Glad to ease your pain.

---

### Post by jamesisin on 2010-03-29
What am I?  The Beater of Dead Horses?

Problems like this and zombies just won't stay dead.

So I had a hdd fail and I've now pulled that drive out of that machine so I can do a warranty exchange.  I boot and am once again in the same boat: busybox and this time it can't find /dev/sde1.  Well no sheet, that's why I told you to use those UUID's.

What gets me is that I am presented with kernel choices and then the Ubuntu white circle splash screen *before* it drops the ball.  Which means it spent a lot of time booting from the correct device before it couldn't find it by looking for it elsewhere.

---

