---
title: "Changing Boot Order. Start up manager won't work"
date: 2011-09-24
forum: General Help
---

### Post by derekreilly on 2011-09-24
Hi,

I have Ubuntu 11.10 and Linux Mint 11.04 installed and am trying to make mint the default OS on boot up. I have tried to change the order in the start up manager in both Ubuntu and Mint, it saves, however on boot up, it always loads Ubuntu as default in the grub.

I would like to have Mint as default at the moment.

Any ideas?

---

### Post by JRV on 2011-09-24
Any of the three methods listed in this thread should work:

[http://ubuntuforums.org/showthread.php?t=1795241](http://ubuntuforums.org/showthread.php?t=1795241)

---

### Post by derekreilly on 2011-09-24
Thanks JRV, sudo gedit /etc/default/grub worked although when I chose number 6 on the list for Mint it went to 7 :)

Of course, choosing 5 took it to 6 and Mint.

Thanks!!

---

### Post by ajgreeny on 2011-09-24
And yet another way is to boot to Mint and run ```
sudo grub-install /dev/sda
```assuming sda is your hard disk that you boot from.  This will replace the ubuntu grub with mint's grub and then, of course mint will be the default OS.

---

### Post by Mark Phelps on 2011-09-24
Just so you know ... startupmanager does not work anymore with the newer GRUB versions.  If you still want to use an app to customize GRUB, you should use Grub-Customizer instead.

---

