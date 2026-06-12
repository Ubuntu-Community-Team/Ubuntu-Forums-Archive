---
title: "wubi 10.04, grub gone, boot crashs, no error message"
date: 2010-07-03
forum: General Help
---

### Post by nitram9 on 2010-07-03
I have a 10.04 wubi install ( I think, at least it's a 10.XX ).  I initially installed it as a 9.10 about 6 months ago and upgraded it a few months ago.  It has been working fine but I just set it to restart after a routine update and it will no longer boot.  

When I select ubuntu from the windows bootloader it should then start grub.  However instead the computer just resets without an error message.

I have booted into windows and checked the ubuntu folder.  ubuntu/disks/boot/grub is now empty.  I have run chkdsk in windows and everything is fine.  I'm worried that the update I erased grub for some reason.

Can anyone help me rebuild the necessary files so that it will start?  Maybe this isn't the problem does anyone have any other ideas.  Is the grub executable supposed to be located in boot/grub or does it just have the menu in there.  Is there anyway for me to boot the image without grub so I can just get back to work (I have a project due tomorrow)?

I do not have access to a blank cd and burner right now so I can't use a liveCD to figure this out.  However if you have suggestions involving a liveCD please let me know so that I can fix it tomorrow.

Thank you in advance.

---

### Post by bcbc on 2010-07-03
Have you seen this link? [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

See if that solves it.

---

### Post by nitram9 on 2010-07-03
No it does not but thank you anyway.  That is for 9.10 only and it involves a case in which either the grub menu is loading or the grub propt loads however I receive neither.  It just resets.  I tried it anyway and it didn't work.

Does anyone know if there is a way to use a live cd to boot the kernel in my image.  If I can run my system then unintall - reinstall grub2 that might fix it but I have no idea how to uninstall - reinstall it from outside the system.

---

### Post by bcbc on 2010-07-03
If you installed it as 9.10 and then upgraded to 10.04 then the wubildr you have came from 9.10.

regarding reinstalling, wubi installs ubuntu on a virtual disk c:\ubuntu\disks\root.disk so you can just copy this somewhere outside of the c:\ubuntu directory. When you uninstall the entire directory is deleted along with the virtual disk and all your ubuntu data.

So as long as it is outside, you can uninstall, reinstall, and then just copy over the backup root.disk on top of the new one.

This will work as long as the problem isn't with the root.disk. You can also boot from a live cd or new install and mount the root.disk to copy over data. see the wubi guide for details. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2010-07-03
I've been running some tests... installed 9.10 wubi and upgraded to 10.04. Found that the boot was failing. Replacing the wubildr (9.10 bug) didn't solve it. 

Even with a grub rescue prompt I couldn't boot it, however, since I have a real install with 10.04 I could manually boot wubi from it's grub prompt. This made me suspect that recent grub-pc updates have introduced incompatibilities with the wubi boot mechanism.

So, I installed 10.04 wubi, replaced the root.disk with the upgraded root.disk I had from before. Now it boots.

I've seen a few threads like this in the past couple of days. But it's hard to tell without feedback.

Anyway... if you got it working maybe you can let me know how, or if you are still trying, consider doing what I did.

The tests take a long time - especially on my test machine which is old - so the more feedback I get, the more it can help others with the problem and get a bug report submitted.

---

