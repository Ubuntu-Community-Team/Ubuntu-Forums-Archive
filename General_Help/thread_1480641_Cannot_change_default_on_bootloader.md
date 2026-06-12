---
title: "Cannot change default on bootloader"
date: 2010-05-11
forum: General Help
---

### Post by ffahog on 2010-05-11
On my netbook (I'm using Ubuntu Netbook Remix, 10.04) the default option in the Grub menu is Ubuntu. Problem: I'd prefer it to be Windows 7.

I've tried using Startup Manager, which I've used successfully in the past. The program loads fine and lets me change all of the options, and saves and closes fine. But when I restart, the bootloader begins with Ubuntu and a 10 second timeout instead of Windows 7 and a 3 second timeout.

I've also tried editing etc/default/grub and, again, I was able to change it and save it without a problem (default menu item: 4, default timeout: 3). I also did a 'sudo update-grub' to try to get it to stick.

Still nothing. Every time I start up the computer, it's set on Ubuntu 10.04 and a 10 second timeout.

Help!

---

### Post by ffahog on 2010-05-11
After some more searching, I found this thread:

[http://ubuntuforums.org/showthread.php?t=1454117](http://ubuntuforums.org/showthread.php?t=1454117)

With this post:


> **padd said:**
> Thanks DRS305, had a look at that post and ran this

```

sudo -i
apt-get purge grub-pc grub-common
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

```

reinstalled startupmanager and it now works as it should

Thanks a lot :)

Padd.


And it worked for me. Problem solved.

---

