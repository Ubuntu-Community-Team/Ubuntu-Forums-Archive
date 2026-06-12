---
title: "Booting to a command line in Ubuntu 10.04"
date: 2010-07-23
forum: General Help
---

### Post by subi211 on 2010-07-23
A quick search of these forums (and others) will show this question to be pretty common.  But I've tried all the suggestions I've found and had no luck:

- Use rcconf and update-rc.d -> These are unused since Karmic.
- Change the runlevel in /etc/inittab -> Did not exist, and when created caused a lock up.
- Edit grub.conf -> Neither it nor menu.lst exist.
- Change stop on runlevel in gdm.conf -> Causes the Ubuntu title screen to lock up, and when ESC is pressed reveals that the boot is stuck on "checking battery state".
- apt-get remove ubuntu-desktop && apt-get autoremove -> No effect.
- apt-get remove gdm -> Kill system and requires reinstallation.

What I want to do is boot into a command line (preferably with no title screen) and then manually run an app in a vanilla X server (using xinit [APP]).

Is this possible?

---

### Post by nothingspecial on 2010-07-23
If you wanted it nice and clean, with no left over configs or libraries, just install the minimal iso.

Or if you want to keep your current installation, this page has a command that removes all ubuntu desktops packages - watch out though, don`t forget to delete the last bit or you will end up with Kubuntu - really.

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by oldos2er on 2010-07-23
If you're using grub2, this is fairly simple to do. Edit /etc/default/grub (gksu gedit /etc/default/grub) and change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="text"
When you're done, run **sudo update-grub**, and reboot.

---

### Post by subi211 on 2010-07-27
Cheers guys, I went with the minimal install (F4 from the Alternative Install CD for reference).  That's just what I wanted, I didn't realise there was one for Ubuntu.  :)

---

