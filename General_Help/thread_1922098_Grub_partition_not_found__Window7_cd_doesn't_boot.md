---
title: "Grub partition not found : Window7 cd doesn't boot"
date: 2012-02-08
forum: General Help
---

### Post by aaditya chauhan on 2012-02-08
I had fedora and windows 7 installed on a dual boot laptop of mine, but I messed up the ati driver installation of my fedora, so I formatted all the linux partitions through windows and rebooted the system, but now when I boot my laptop I get grub partition not found >> grub command-line, I thought that by windows recovery option through vaio care, i would be able to get it back, but even that didn't work. I googled and found that I need to boot through windows 7 recovery discs, I did that but, it isn't booting from the CDs, even though I had made boot from CDs and optical drives the first choice in my bios, I have lost all my data, and I cant use my computer now, I am panic-ing, plz helpRegards

---

### Post by sikander3786 on 2012-02-08
Welcome to the forums. :)

Grub has nothing to do with CD/DVD booting. If your Bios is properly set and your optical drive is working, there isn't anything that would stop you from booting the Windows 7 recovery discs.

Make sure your CD/DVD drive is in proper working condition and also re-check your Bios settings. There should be a boot-options key displayed on the Bios screen, hitting which lets you choose your preferred boot device.

And if you yourself burnt the Windows 7 recovery discs, make sure your chose 'Burn image to disc' option while burning rather than 'Data disc'.

---

### Post by jamesisin on 2012-02-08
It sounds like you were using Grub as your bootloader.  When you formatted your Linux partitions you of course deleted all the files Grub would be seeking at boot time.  If you rebuild another Linux installation you will be working toward fixing Grub.

I recently had to sort out a Grub and Windows 7 problem which you can read about here:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

You may be able to use your Windows installation media to rebuild the Windows boot loader (to replace Grub), and there is a little information about in the article as well.

As long as you proceed with caution you ought to be able to recover your Windows data.

---

### Post by Mark Phelps on 2012-02-08
Try using Boot-Repair to restore the Windows boot loader:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

