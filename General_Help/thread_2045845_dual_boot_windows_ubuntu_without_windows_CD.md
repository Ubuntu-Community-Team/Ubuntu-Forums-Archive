---
title: "dual boot windows ubuntu without windows CD"
date: 2012-08-22
forum: General Help
---

### Post by diamantis13 on 2012-08-22
Hi,

I have a lenovo thinkpad X230T that came with windows7 installed. Before wiping out the disk and doing a fresh linux installation I wanted to make a dual boot for a while.

The problem is that I don't have any windows CDs to repair the MBR after installing grub because windows was preinstalled.

Any suggestions on what to do?

thank!

---

### Post by roger_1960 on 2012-08-22
Hi
I did not need windows disks to install 12.04 as dual boot, but I did have to make some space as my W7 was using all 4 primary partitions.

---

### Post by mikechant on 2012-08-22
> The problem is that I don't have any windows CDs to repair the MBR after installing grub because windows was preinstalled.

You only need the Windows CDs if you are *removing* grub (e.g. deleting Ubuntu and going back to single boot Windows).

Also, there may be a utility included in Windows to create a recovery CD.

---

### Post by Frogs Hair on 2012-08-22
> Also, there may be a utility included in Windows to create a recovery CD.

This option is included with Windows, and it is possible with a USB also. I found many posts like the following. [http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by Mark Phelps on 2012-08-22
Win7 has a feature, as part of the Backup option, to create and burn a Win7 Repair CD.  Using that, you can not only repair startup problems, you can also restore the Windows MBR.

---

### Post by SJR Dorset on 2012-08-22
You can also install EasyBCD on your Windows installation and use it to rewrite the MBR and add new entries to you boot menu:

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

It's free for non-commercial use.

---

### Post by diamantis13 on 2012-08-22
Thanks for the advice. I couldn't burn a windows recovery CD (my laptop doesn't have a CD burner) so I gave up and now I am doing a fresh install.

---

