---
title: "attempting to modify grub boot"
date: 2010-02-21
forum: General Help
---

### Post by henners91 on 2010-02-21
Hi guys, i'm new to ubuntu but have used fedora a bit. just installed ubuntu on my eeepc 1000he, it looks awesome so that's really good. I'm trying to speed up boot time by reducing the countdown for dual boot. gksu gedit /boot/grub/menu.lst this is the command i enter and it says that it does open the file, however the file shows no text, it's blank and there's no option to scroll down past anything?! i can't figure out why it's not showing all the boot info?!
 Thanks for any help given :)

---

### Post by Barriehie on 2010-02-21
Let's see what version of grub you have:
```

sudo grub --version
```

---

### Post by oldfred on 2010-02-21
If you do not have menu.lst and it boots it just about has to be Karmic as a clean install with grub2 unless you typed the edit command wrong.

See instructions on editing /etc/default/grub:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Grub2 info by ranch hand and many links to other grub2 info sites 
[http://ubuntuforums.org/showthread.php?p=8191211](http://ubuntuforums.org/showthread.php?p=8191211)

---

### Post by henners91 on 2010-02-21
Thanks for the help.
 I'm running 9.10 karmic and didn't know that the grub file i was looking for is in /etc not /boot
 thanks again

---

