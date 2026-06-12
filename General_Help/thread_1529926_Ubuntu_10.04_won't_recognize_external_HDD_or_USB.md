---
title: "Ubuntu 10.04 won't recognize external HDD or USB"
date: 2010-07-12
forum: General Help
---

### Post by yoruga221 on 2010-07-12
I'm trying to restore my laptop through the Ubuntu 10.04 Live CD. A while ago, Windows 7 died. I've tried everything possible to make it work again to no avail. At first I gave up on recovering my files and proceeded to formatting it, but that didn't work either, although it would boot from the CD, it would get stuck. It's as if the HDD couldn't be accessed.

After trying almost every version of Windows available, I decided to give Ubuntu a shot. I have used Ubuntu before and I thought maybe I could use the Live CD to see whether I could access the HD or not and, if not, claim the warranty (I bought the computer 4 months ago). I downloaded Ubuntu 10.04 and booted from it and was able to access all my files.

I wanted to move my files to an external HDD through the USB, but I plugged it in and nothing happened, no icon appeared on the desktop or on the Computer directory. I plugged in a normal USB flash drive, and no icon appeared. The funny thing is that the USB led lit up, so I knew it was connected to the computer.

I thought maybe Ubuntu wasn't mounting the drives and that I had to do it manually, so I ran both the lsusb and fdisk -l commands on the terminal with both drives plugged in and neither of them appeared listed. I even opened the message log to see if there was some reaction when I plugged it in, but nothing worked. :S

I restarted the computer and opened the BIOS to see whether the USB drive was enabled, as I had previously disabled some options trying to restore Windows, but the external HDD was being recognized by the computer; on the boot list it showed the name and serial of the drive, so that wasn't it.

I downloaded previous versions of Ubuntu, thinking maybe it had something to do with that (although I know it shouldn't), and the same thing happened: I could access the internal HDD but the external drives weren't being recognized.

I've browsed through the forums, going over the same procedures as other people with the same problem, but nothing works for me and now that I know that my files are safe, I don't want to format it anymore before saving at least the most important ones ><

I think I have 2 options before I run out of ideas. I could use GParted or Partition Editor from the Live CD to resize the partition to make enough space to install Ubuntu on my computer (I was thinking of doing it, anyway) and then fix everything from there instead of from the Live CD (if that changes anything), but I'm afraid that the files in the partition could become corrupted or damaged, and I don't want that. The other option would be to install Ubuntu on the external HDD and boot from it, as it WOULD HAVE to recognize it.

I want to know if there is any way to solve it before resorting to the latter option, as the HDD is not mine and I don't feel right partitioning it.

Thanks for your cooperation.

---

### Post by bobcollard on 2010-07-12
What is the format of the external drives?  A live CD may not recognize NTSF, but it will recognize FAT32.

---

### Post by pricen2 on 2010-07-20
I had a similar problem with Ubuntu 10.04 live (but running from a USB drive) and also on a complete 10.04 harddisk installation. No other USB drives would be recognised, despite the activity lights flashing, and even when they were occasionally recognised they wouldn't auto-mount.
 
Searching a few forums, I saw that other people who experienced this USB issue had got around it by disabling their floppy drive and/or floppy drive controller in BIOS.
 
I did this and now all USB drives are almost instantly recognised and auto-mounted! Also, the harddisk installation boots alot quicker too now.
 
Give it a try.

---

