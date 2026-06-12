---
title: "Ubuntu 9.10 big problems"
date: 2009-11-13
forum: General Help
---

### Post by macjorgen on 2009-11-13
Hi all!

After upgrading to Karmic (9.10) I've experienced quite a lot of problems:

- The boot time has doubled(ish) and the machine is generally running slower.
- Won't suspend. Does it once after install, then the PC freezes with black screen every time with me having to hold down the shutdown button for 5 sec. then start it up again.
- The volume won't go all the way to 100%. Drops down 20% as soon as i click on the panel-icon.

I did a fresh install as well, but it didn't help. For me now Jaunty (9.04) is running a lot better and smoother than the latest release. Why is it that Ubuntu seem to work excellent on some computers and not at all on others??? Help anyone???

Cheers,
MacJ

---

### Post by kio_http on 2009-11-13
Too be able to provide help. Your computers hardware specs would be required. 

Cpu?
Motherboard?
Hard disk?
Graphic card?
Ram?
Pci cards?
IO controller?

---

### Post by macjorgen on 2009-11-13
Ok, sorry about that.

This is the only information I have about the machine:
Hope it helps...


- AOPEN Case H500Y WO/PSU Midi Tower Black USB/AUD/1394 PC Production Only
- CHIEFTEC PSU 560W ATX 12C 2.2/EPS-12V 12cm Fan PFC Cable Management
- ASUS Mainboard S-775 iP965 ATX Audio GbLAN SATA Raid Retail
- INTEL CPU Core 2 Duo E6300 1.86GHz S-775 1066MHz 2MB "Conroe" Boxed
- GEIL 2GB (2x1GB) PC6400 DDR2 800Mhz BGA Brushed Aluminum Heat Spreader Retail
- ASUS VGA-Card Radeon RX1600PRO 512MB PCI-E DVI TV-Out Heatsink Retail
- WD Harddisk 160.0GB 7200RPM SATA II 3.5" 8MB
- SAMSUNG DVD Recorder 18x +R/+RW -R/-RW DVD-RAM Black Bulk With Software
- CC FireWire 1394 Low Profile 2xExternal 1xInternal PC/Mac PCI


Cheers,
MacJ

---

### Post by kio_http on 2009-11-13
Try not using swap and resetting your bios to default.

also once booting produce terminal output for

```
dmesg
```

---

### Post by macjorgen on 2009-11-15
Hi!

Not really sure what you mean about not using swap??
By the way, just installed Karmic on my Asus eeePC 1000H and it works like a charm. Maybe my desktop PC is too old??

Cheers
MacJ

---

### Post by tommcd on 2009-11-15
> **macjorgen said:**
> 
- The boot time has doubled(ish) and the machine is generally running slower.

I have seen quite a few people reporting much slower boot times with Karmic. I have done a lot of searching, and have not found any definitive solution. Does anyone know about this? 
 Sorry I don't have an answer for this problem. I just want you to know that you are not the only one reporting this.
You may want to install **bootchart** and see where the bootup is slowing down. I don't know much about interpreting bootchart logs, but if you post the output here, that may aid in diagnosing the problem.
See this article about bootchart:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_boot_perf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_boot_perf&num=1)
As for the volume not going to 100%, have you tried using **alsamixer** in the terminal to increase the volume? If not, try it and see if you can raise the volume level.

---

### Post by girto on 2009-11-15
Did you update your Karmic?
Karmic boot times have got faster.

Furthermore, with the inclusion of ureadahead (due soon i suppose, or can be installed from a ppa), boot time has never been as fast for many people.

---

### Post by tommcd on 2009-11-16
> **girto said:**
> Did you update your Karmic?
Karmic boot times have got faster.

This is true. I installed Karmic from the beta CD. I did notice that it took a bit longer to boot. It was not so long that I thought it was a problem though. But since Karmic moved through RC to final I have noticed that boot times have improved.
Ironically, one of the goals of Karmic and Lucid 10.04 is improving boot up times:
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_boot&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_boot&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=NzMxMw](http://www.phoronix.com/scan.php?page=news_item&px=NzMxMw)
 There have been many changes to the way Ubuntu boots. There are the upstream changes to kernel mode setting for intel and ATI graphics, to the move to grub2 and upstart and probably many other things as well. I suppose it may will take some time to work out the kinks in this stuff.

---

