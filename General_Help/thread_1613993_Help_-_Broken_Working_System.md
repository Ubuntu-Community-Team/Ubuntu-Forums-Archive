---
title: "Help - Broken Working System"
date: 2010-11-05
forum: General Help
---

### Post by Quarkrad on 2010-11-05
Ubuntu 10.10.  There was a long list of 'linux images' in the boot screen so once booted into system via Synaptic I searched for linux-image and removed the early ones.  Problem now is - when I boot I get the screen showing 2.6.32-25 generic and 2.6.32-25 (recovery mode) as well as 2.6.32-24 generic and 2.6.32-24 (recovery mode) but when I click on them nothing happens - the screen sits there looking at me.  No matter what I do I cannot boot to Desktop.  As a newbie - what is the best course of action at this point?

---

### Post by dcstar on 2010-11-05
> **Quarkrad said:**
> **Ubuntu 10.10**.  There was a long list of 'linux images' in the boot screen so once booted into system via Synaptic I searched for linux-image and removed the early ones.  Problem now is - when I boot I get the screen showing 2.6.32-25 generic and 2.6.32-25 (recovery mode) as well as 2.6.32-24 generic and 2.6.32-24 (recovery mode) but when I click on them nothing happens - the screen sits there looking at me.  No matter what I do I cannot boot to Desktop.  As a newbie - what is the best course of action at this point?

10.10 does not use 2.6.32-25, 10.04 does. The current 10.10 kernel is 2.6.35-22.

You either are not booting the right OS or the 10.10 kernels actually in the system are not in the Grub menu.

More information required, **exactly** how did you install 10.10 and **exactly** what did you remove?

---

### Post by Quarkrad on 2010-11-05
Ah - this is the 5th machine I look after (family members) so I think I've got confused with this one.  Perhaps it is 10.04.  I'm away from home and do not have my discs with me so in antisipation I burnt a LiveCD.  Anywhay - to answer your question.  I have done this before on other machines - when multiple images are installed via the update manager you get a longer list at boot.  So - once the syste is settled I tend (rightly or wrongly) to delete load images via Synaptic to keep the list short.  From what I can remember it was just old images.  The new 10.10 LiveCD I just burnt (perhaps I need to burn another - 10.04) starts to load but stops for some reason saying:  **BusyBox v1.15.3 (ubuntu 1:1.15.3-1 ubuntu5) built-in shell (as)  (initramfs) cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs**   - I have never seen this before.   I was hoping to LiveCD into the system and copy **home** to another partition on the PC before attempting anything.

---

### Post by Quarkrad on 2010-11-05
OK - that error is to do with doggy images from the ubuntu site.  Just imaged new LiveCD.  Could have done without that!

---

### Post by Quarkrad on 2010-11-06
Re-built system - clean install

---

