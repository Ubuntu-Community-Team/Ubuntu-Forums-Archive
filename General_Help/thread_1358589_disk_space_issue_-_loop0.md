---
title: "disk space issue - loop0?"
date: 2009-12-18
forum: General Help
---

### Post by raghuvansh on 2009-12-18
First off - I'm new to Ubuntu and command lines scare me. Please keep everything as simple as possible :)

I created a dedicated 65GB partition on my HDD using Windows 7 and I'd installed Karmic via Wubi on it once. It was working fine, then I updated the kernel and there was a well-documented issue with GRUB which locked me out of the OS, so I uninstalled and reinstalled Karmic on the same partition, again via Wubi. Installed the kernel updates again, this time I updated GRUB.

Now this second install it works fine, except it keeps telling me the disk space is filling up and I have only 180MB free space. A little fishy because it's a dedicated 65GB partition and I have hardly any software installed. So I checked the filesystem through system monitor, turns out there's something called /dev/loop0 which is 3.6GB and nearly full. There's also a /dev/sda5, which I presume is the rest of my partition, and this has 60GB free. Obviously sda5 is where I want my Ubuntu to be running and apparently it isn't, it's running on loop0 instead.

What exactly is going on and how can I get this loop0 thing out?

---

### Post by DJonsson2008 on 2009-12-18
Is there anyway you can install Ubuntu onto another drive.

I've found loading Ubuntu in a dual boot situation to hardly
worth the complications involved when 2nd HD prices being so
low for the 40-80 gig drives needed for an Ubuntu system.

---

### Post by raghuvansh on 2009-12-18
Nope. I'm on a laptop, actually, so no adding new drives or anything.

---

### Post by DJonsson2008 on 2009-12-18
The latest version of GParted live would help you in 
resizing the partitions. Its though impossible to 
recommend anything without first letting you know
everything should be backed up before you move forward
with any resizing strategy.

Assuming you have your essential data and files backed
up you should be able to reduce and stretch the partitions
with Gparted as needed. 

I'm not familiar with Wubi. USB to IDE/SATA or other cabling
adapters/interfaces can provide external bootable drives for laptops. If you find working the partitions too difficult
but still want to run Ubuntu as well as windows you might
consider an external drive. 

Installing Ubuntu on a blank drive using their default use all drive space option has always worked well for me. As a beginner attempting dual-boot and other schemas, although they seem to be popular -- were always more trouble than they were worth in the end.

---

### Post by DJonsson2008 on 2009-12-18
BTW Gparted Live CD provides an easy to understand GUI.

---

