---
title: "Problems with default resolution"
date: 2010-05-02
forum: General Help
---

### Post by robertborner on 2010-05-02
Hi all,

I have recently installed ubuntu as my main operating system, everything has been working great except every time I re-boot the resolution resets back to a default. How can I get it to default to 1440x900?

---

### Post by dino99 on 2010-05-02
sudo gedit /etc/default/grub

 add or change

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep

then sudo grub-mkconfig && update-grub

sudo dpkg --configure -a

---

### Post by robertborner on 2010-05-02
Thanks for that, unfortunately when I boot up it still goes to 1024x768 my text in the grub file looks like this, 

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1440x900
GRUB_GFXPAYLOAD_LINUX=KEEP

It has the correct resolution at the login screen but once I log in the resolution goes to 1024x768

---

### Post by dino99 on 2010-05-02
hm, i've seen several bugs reported on launchpad about grub problem with the latest .iso image

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/503935](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/503935)

i think you could remove/purge every grub packages installed with synaptic, then reinstall only grub-pc and grub-common and install it (when asked) on your mbr lucid partition (/dev/sda or so, you have to know it exactly)

have you configured startup-manager (system admin) ?

---

