---
title: "Help! boot menu of windows8 and ubuntu 12.04 does not show"
date: 2012-08-28
forum: General Help
---

### Post by Jovenrp on 2012-08-28
I installed windows 8 and ubuntu 12.04 in my desktop (windows 8 first installed) and now whenever I boot my pc no choices of OS appears. It just boot directly to ubuntu 12.04. I tried the pressing of shift keys or the esc key on startup but still no success.

I tried running a boot repair and here is my pastebin:

[http://paste.ubuntu.com/1172977/](http://paste.ubuntu.com/1172977/)

Pls. Help asap. Thanks!

UPDATE:

I run the script

sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2

and run boot repair again. Here is my new pastebin,

[http://paste.ubuntu.com/1172992/](http://paste.ubuntu.com/1172992/)

Thanks again!

---

### Post by oldfred on 2012-08-28
I do not see anything wrong in boot script report.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

But deleting the hiberfil when Windows expects to load it on reboot, I would think would corrupt Windows.

---

### Post by Bucky Ball on 2012-08-29
Have you tried hitting shift after the BIOS screen when you boot? Should bring up a menu but your prob could be more involved than that, as oldfred alludes to.

---

### Post by Jovenrp on 2012-08-29
> **Bucky Ball said:**
> Have you tried hitting shift after the BIOS screen when you boot? Should bring up a menu but your prob could be more involved than that, as oldfred alludes to.

Yes I already tried that but still no menu. Now I have a new problem, I used the boot repair while in ubuntu and changed the default OS to windows 8. Now I am able to use windows 8 but I don't know how to turn back to ubuntu. :(

I already checked the Control Panel -> System and Security -> System -> ( left side ) Advance System Setting -> Startup and recovery -> go to settings. The default OS that appeard is windows 8. :(

---

### Post by Bucky Ball on 2012-08-29
Can't help with Windows but you could use Boot Repair to make Ubuntu the default OS then open a terminal and:

```
sudo update-grub
```Then reboot.

Have you tried the shift key at boot again since you used Boot Repair? If it's booting anything it has probably fixed your grub and that may work now.

---

### Post by YannBuntu on 2012-08-29
Hello
> **Jovenrp said:**
> no choices of OS appears. It just boot directly to ubuntu 12.04.

Please:
1) run Boot-Repair
2) Click "Advanced options"
3) Go to the "GRUB options" tab, tick the "Uncomment GFXMODE" option
4) Click the "Apply" button. Write the new URL on a paper.
5) Reboot and tell us what you observe (and the new URL)

---

