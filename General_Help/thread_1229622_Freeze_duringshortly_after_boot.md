---
title: "Freeze during/shortly after boot"
date: 2009-08-02
forum: General Help
---

### Post by eyescrm on 2009-08-02
Hey there.

For a while now my ubuntu has seemingly randomly (happens in about 2/7 boots) gotten stuck during (at the ubuntu logo screen, bar will be stuck at about 15%) or shortly after (within about a minute) booting. My keyboard and mouse lights will go out (both usb) and I am forced to hard reboot. After the hard reboot it will work fine.

If it boots normally right away or after a hard reboot my system will not freeze during normal use, e.g. playing games, having lots of apps running etc. Freezes occasionally occur during/shortly after boot only.

Any ideas other than reinstalling ubuntu?

---

### Post by eyescrm on 2009-08-02
anyone?

---

### Post by jamesrl on 2009-08-02
You could try editting /boot/grub/menu.lst (e.g., sudo gedit /boot/grub/menu.lst ) to get rid of the word quiet (and also the splash) in the kernel options that you load, so the line that you boot off of like:

```
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
```

becomes:

```
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro
```

that way you could tell us at least what part of the boot-up sequence seems to be freezing your computer or if there are any error messages that arise.
The quiet option suppresses messages, and the splash option displays the ubuntu logo graphically while booting.

(Don't change the root part or the linux kernel part and it is probably a good habit to make a backup copy before editing system files).

---

### Post by eyescrm on 2009-08-02
Thanks for your reply.
I've changed the file accordingly and I hope it'll return something useful when it happens again.

---

### Post by eyescrm on 2009-08-13
It has happened again, twice. Once after having successfully booted and today during the booting procedure.

The last lines before it froze:

*Skip starting firewall: ufw (not enabled)... [OK]
*Configuring network interfaces... [OK]
*Setting up console font and keymap... [OK]

I've googled and found a few results, yet nobody seemed to have it only occasionally and none of the suggested fixes I found applied to my situation.

---

### Post by zkriesse on 2009-08-13
What version and Linux type are you running? type uname -a in terminal and paste results here.

---

### Post by eyescrm on 2009-08-13
I'm using Linux 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux.

The problem occured in 2.6.28-13-generic as well. I don't think it occured before that.
Also, I tried fsck and memtest, both were fine.

---

### Post by FRuMMaGe on 2009-12-17
[Workaround]("http://ubuntuforums.org/showthread.php?p=8516423#post8516423") (for me anyway. Currently can't confirm this works on any other system)

---

