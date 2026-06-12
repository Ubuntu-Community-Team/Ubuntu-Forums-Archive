---
title: "Ubuntu Doesn't Read Win 7 Disc"
date: 2010-07-25
forum: General Help
---

### Post by narnia_fan12 on 2010-07-25
I've had some problems with my ubuntu lately (>.<) and would like to use my Windows 7 disc to install windows side by side with ubuntu (for compatibility reasons). The problem is, my computer won't boot the disc on startup, won't read it at all, and thus I can't install it. How can I make Ubuntu read the Windows 7 disc? All other discs work fine. 

Its not just my disc- I've used this disc on other computers no problem, and my Ubuntu reads other discs without any problems.

---

### Post by jerenept on 2010-07-25
There is no easy way to install Windows and keep Ubuntu. The Windows boot-loader does not support Operating systems other than Windows.

Maybe you need to change the BIOS settings to enable booting from the optical drive. Is the disc load when Ubuntu has been booted already?

---

### Post by limestone on 2010-07-25
If you're going to install windows you must boot with the cd.. Check if your BIOS is set up for boot cd first.

---

### Post by narnia_fan12 on 2010-07-25
My Bios is set to boot from optical disc. 

So... in other words, I'm completely blocked out from running it on boot?

---

### Post by limestone on 2010-07-25
> **narnia_fan12 said:**
> My Bios is set to boot from optical disc. 

So... in other words, I'm completely blocked out from running it on boot?

Sorry, read wrong... If it's set to optical drive = cd/dvd it should boot your cd.. Maybe you have to press a button to start the windows cd like in xp?

---

### Post by wilee-nilee on 2010-07-25
> **jerenept said:**
> There is no easy way to install Windows and keep Ubuntu. The Windows boot-loader does not support Operating systems other than Windows.


This is not true, you can install windows before or after Linux, in a preformatted partition and then reload the mbr with grub, easily.

Thread starter you need to with a live ubuntu cd shrink the Ubuntu partition set, then make a ntfs partition for W7 to install to with gparted on the live cd. In order to change the Ubuntu partitions you need to turn the swap off.

Then boot the W7 DVD with a key prompt to choose the boot device install then reload grub in the mbr with this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Last of all you need to be aware of maximum partitions allowed on your HD, 4 primaries, or 3 and a extended; that can have more then the max primaries inside. Windows cannot be in a extended though.

You are not blocked from running the W7 install disc it will probably take the boot from key prompt to get you to be able to boot the W7 disk, my prompt is f12 yours could be any f key or esc.

---

