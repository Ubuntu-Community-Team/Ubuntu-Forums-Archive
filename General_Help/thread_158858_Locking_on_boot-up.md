---
title: "Locking on boot-up"
date: 2006-04-11
forum: General Help
---

### Post by Adamsmasher23 on 2006-04-11
I recently installed Breezy 5.10 on my USB HDD.  It took me a while, but I got it running.  I had succesfully booted it up several times, and was working on configuring my Conexant winmodem.  When I was trying to get my modem to work, I installed some packages, including two linux kernel header packages.  The next day when I went to boot, it locked up on the splash while loading 'Starting hotplug services'.

I did a little troubleshooting.  First, I tried to boot it up into rescue mode.  It once again locked up, but I could see on the terminal that it had complained alot about shpchp being missing - and also complained that the shpchp module was missing from the kernel.  I looked at the (few) other posts with people having trouble booting, and went through my BIOS options to make sure I wasn't having conflicts; even though I wasn't before; but I did turn off quick boot.

I would appreciate any help that I could get to fix Ubuntu - reinstalling is not preferred as configuring Ubuntu with a USB HDD is quite lengthy.

My system is as follows
Dell XPS 400
P4 Pentium D Dual core 2.80 ghz
1.0 GB Ram
Removable HDD Western Digital 120 GB - 30 GB ext3, 3.0 gb swap, 97 gb fat32
internal 160 gb Maxtor NTFS
Linux kernel 2.6.12-9-386

---

### Post by thunderduck3141 on 2006-04-11
i think your problem is that u installed the wrong headers, which is causing ubuntu to freak out
try and see if u can use a live cd to remove the packages
hope that helps

---

### Post by Adamsmasher23 on 2006-04-11
To remove it, can I just delete it, or should I attempt to use dpkg -r ?

---

### Post by Adamsmasher23 on 2006-04-11
Well, I booted up off the Live CD, and tried a couple of things.  First, I tried to remove the extra headers, using both dselect and aptitude, but neither of them said that I had any kind of header installed.  I also went to the directory where they had been installed and they weren't there.  I then followed the instructions from [http://doc.gwos.org/index.php/Speed_up_boot]("http://doc.gwos.org/index.php/Speed_up_boot") and disabled hotplug-net, and also put hw_random and shpchp in the blacklist, but it still wouldn't boot.
I don't know what else to try.  Any help would be appreciated.

---

### Post by thunderduck3141 on 2006-04-12
at this point im going to need a print out of when it locks up and a few seconds before that
i dont like the fact that your headers just disappeared, try installing the correct headers and reboot
if that doesnt work feel free to im me 
my screen name is thunderduck3141
peace

---

