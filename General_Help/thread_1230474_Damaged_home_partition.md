---
title: "Damaged home partition"
date: 2009-08-03
forum: General Help
---

### Post by arqbrulo on 2009-08-03
Hi to all. Ok, here's the thing. I decided to finally get rid of my Window's (sda2) partition and give that extra space to my /home (sda3/ext3) partition. I booted my laptop using a live-usb (Karmic). Everything was moving along quite well. I had my lid closed... I was afraid my battery would run out of juice, so I decided to plug in my laptop. Well, Ubuntu, by default, is configured to go to suspend mode when the lid is closed and on AC power. I was not able to wake up my computer after that, and had to reboot (using alt+SysRq+REISUB). After booting back to the live-usb and opening gparted, it showed my home partition as "unknown". Yes, I know I should have backed up my files first. Yes, gparted even warned me of the dangers of changing the partition table. I ignored my own feeling and the advice my pc gave me. Now I need to find a way to recover everything from my (formerly) ext3 partition. Any help is very much appreciated. :???:

---

### Post by arqbrulo on 2009-08-03
Well, I'm sure that those of you who read my question, honestly had no idea what I was talking about or did not know how to help. I'm also sure that there was at least one person out there who might have been able to help, but did not read my question. Anyways, good news. I ran testdisk from the liveusb and restored my partitions. Evrything is there like it should. I did not loose anything. Well, at least that's what I think, I have not checked everything yet.

---

