---
title: "&quot;gave up waiting for root device&quot; while booting"
date: 2010-10-10
forum: General Help
---

### Post by ChaosChris2009 on 2010-10-10
I installed Ubuntu 10.10 inside Windows 7 today, Ubuntu 10.10 finished installing and all just fine

but when I try to boot into Ubuntu 10.10 from the boot menu I get this error

"gave up waiting for root device" while booting

and it mentions something about BusyBox

Help?

---

### Post by lukeaw on 2010-10-10
Same deal here, I freshly installed UNR 10.10 on my Lenovo S10-2  writing over Ubuntu 10.04, alongside Windows 7. The full message is:

```
Gave up waiting for root device. Common problems:
 - Boot args (cat /prov/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/sdb7 does not exist.  Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

I was a bit wary during install because I created a logical partition ~200MB ext2 for /boot to sit on, followed by a ~70GB btrfs partition for /, then ~3GB for swap space.
If I remember correctly these were /dev/sdb6 /dev/sdb7 and /dev/sdb5 respectively, so the alert in the message seems to refer to my swap space (though I will check this) [COLOR="Red"]- Edit: corrected; /boot / and swap are 6, 7 and 5, but are actually on /dev/sda[/COLOR]

---

### Post by lukeaw on 2010-10-10
Update: I installed from a USB flash drive, which I assume was  assigned /dev/sda during installation. However, now I've completed the installation and removed the flash drive my main hard disk is /dev/sda, which is why I was getting the above boot error. I've edited grub's config from the shell as follows and it's got me a step further:

```
$ mkdir -p /mnt/boot
$ mount /dev/sda6 /mnt/boot
$ grep -F /dev/sdb7 /mnt/boot/grub/*
/mnt/boot/grub/grub.cfg:        linux   /vmlinuz-2.6.35-22-generic root=/dev/sdb7 ro   quiet splash
/mnt/boot/grub/grub.cfg:        linux   /vmlinuz-2.6.35-22-generic root=/dev/sdb7 ro single
$ sed -i -e 's#/dev/sdb#/dev/sda#g' /mnt/boot/grub/grub.cfg
$ reboot
```

I'm now staring at the more friendly graphical boot screen but not quite at the desktop yet; "The disk drive for /boot is not ready yet or not present", "Continue to wait; or Press S to skip mounting or M for manual recovery"

---

### Post by lukeaw on 2010-10-10
Final update: I'm sure the gurus out there were shouting the answer out loud at their screens :)

I figured /boot wasn't being found so pressed M which dropped me to a shell. I corrected the fstab with the same sed command.

```
$ sed -i -e 's#/dev/sdb#/dev/sda#g' /etc/fstab
$ reboot
```

...And I'm now playing with the shiny new Unity interface!

@Chris: I hope you're able to get something out of my posts here, shout if you need anything clarifying. To summarise: find and mount your partition containing grub, see where it's looking for your root filesystem. If it's not correct you've found your problem :)

---

### Post by ABitTooSpicy on 2011-07-08
lukeaw, I am getting the same exact error except mine says "ALERT!  /dev/**sda1** does not exist.  Dropping to a shell!"

Could you walk me through the fix?  (pretend you are talking to a 5 year old!) :)

---

### Post by wildmanne39 on 2011-07-08
> **ABitTooSpicy said:**
> lukeaw, I am getting the same exact error except mine says "ALERT!  /dev/**sda1** does not exist.  Dropping to a shell!"

Could you walk me through the fix?  (pretend you are talking to a 5 year old!) :)Hi, did you install ubuntu with wubi like the orginal poster did? if so have a look at this link.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by lukeaw on 2011-07-12
> **ABitTooSpicy said:**
> lukeaw, I am getting the same exact error except mine says "ALERT!  /dev/**sda1** does not exist.  Dropping to a shell!"

Could you walk me through the fix?  (pretend you are talking to a 5 year old!) :)

How did you install Ubuntu - from the live CD or from a USB flash drive?

On a possibly related note I've noticed that even with 11.04 if you have an ISO image stored on a flash drive and boot from that, the installer still offers to unmount it before proceeding :confused:

---

