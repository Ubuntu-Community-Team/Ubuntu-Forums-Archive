---
title: "update-grub not updating boot menu"
date: 2010-07-02
forum: General Help
---

### Post by faithfracture on 2010-07-02
Ubuntu 10.04 x64
 
Did a fresh install on Monday this week and ran updates. On Monday, I was able to edit the grub.d scripts and /etc/default/grub and run update-grub and grub.cfg would change accordingly and my boot menu would show the changes in grub.cfg.
 
Today, I am trying to make changes to grub, and when I run update-grub, my grub.cfg file does update properly, but when I reboot, the menu entries do not change.
 
Already tried purging & reinstall grub, but that didn't fix the problem.
 
Does anyone have any ideas what's going on here or have any other suggestions I might try to get this fixed?
 
Thanks.

---

### Post by oldfred on 2010-07-02
Do you have more than one install?. That would explain a grub.cfg getting updated but you are booting a different install.

This will tell what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by faithfracture on 2010-07-02
No, only the one install of Ubuntu. Figured out what was going on anyways though. Somehow, MBR for SDA got messed up. Just had to run grub-setup and set it to /dev/sda and it's working again. I don't have a clue what would have screwed up the MBR. Oh well.

---

### Post by philinux on 2010-07-02
> **faithfracture said:**
> No, only the one install of Ubuntu. Figured out what was going on anyways though. Somehow, MBR for SDA got messed up. Just had to run grub-setup and set it to /dev/sda and it's working again. I don't have a clue what would have screwed up the MBR. Oh well.

Have a look through your bash history. You may have done something.

~/.bash_history

---

