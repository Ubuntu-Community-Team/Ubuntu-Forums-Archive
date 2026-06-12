---
title: "Running an iso file"
date: 2010-12-12
forum: General Help
---

### Post by bdemers on 2010-12-12
Possible to run an iso file such that it will install into a different partition?  I have a dvd iso for BackTrack that I want to install in an old, unfriendly server.  Options very limited, so I thought that if a booted a LiveCd, copied the iso to a file on a small hard drive partition, I could somehow run that iso file and install the dvd image to yet a different partition making that partition bootable so that when I yank the LiveCd, the server would boot from the new installation.  Two separate hd's would probably be best, here.

I would need to figure out how to launch the iso image to start the install.
Any clues

---

### Post by Foxheadz on 2010-12-12
Can't you just install it from the LiveCD

---

### Post by bdemers on 2010-12-12
I'd love to, but what do you mean exactly.  With the Live CD I can download the dvd iso, but then what do I do?

---

### Post by Foxheadz on 2010-12-12
Well if your using backtrack r4 just burn the iso to the dvd boot into it and then run the install script on the desktop

---

### Post by bdemers on 2010-12-12
That's the interesting part.  This server doesn't have a dvd reader, only cd.  It doesn't have an ide connector so I can't just plug in a dvd as a quasi internal.  It doesn't boot from usb, the bios doesn't support that.  I can run scsi, but I do not have a scsi dvd player. 

Like I said in the beginning, old and unfriendly.:(

---

### Post by matt_symes on 2010-12-12
Hi

> old and unfriendly.Your not joking. I have never used backtrack so i have no idea what its installer is like.

You can use grub to boot into an iso stored on a partition, so if you could put the DVD onto a small partition and set up grub maybe it could boot it and then you can install.

Booting an iso from grub (Read the caveat at the start though. Not all ISO's will work.)

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

Best of luck. And please post back how you get on. I'm really interested.

Kind regards

---

### Post by bdemers on 2010-12-12
BackTrack is a specialized Linux distribution used for security maintenance.  Since it is a kernel and a gui, you could load up Rythmbox and listen to music on it if you wanted to.

---

### Post by oldfred on 2010-12-12
I have not used this script, but it creates USB boots using grub2 to boot many systems.

When looking at the script, he extracts the casper, kernel and initrd for Back-Track, so it is not one that will directly loop mount. You have to install the kernal to boot then loop mount it to run the ISO.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by bdemers on 2010-12-12
Thanks, people.  After considering what I need to go through to get this dvd iso going, and after looking at what hardware I have to support, I have just got done purchasing a scsi dvd-rom drive.  It made the most sense.

I'm going to close this now, but not before once again saying thanks for the input.  I will look closely at the boot usb for other uses .  That is enticing.

---

### Post by matt_symes on 2010-12-12
Hi

> I have just got done purchasing a scsi dvd-rom drive.  It made the most sense.

That's a good call. ;) Always take the simplest option wherever possible.

Kind regards

---

### Post by oldfred on 2010-12-13
I thought somewhere someone had posted the list of applications to install into Ubuntu so you had all of backtrack in Ubuntu. I am pretty sure it was in the forums in the 3 or 4 months.

---

### Post by bdemers on 2010-12-13
Thanks for the heads up, I'll go searching.  There are several suites out there, most list the apps that they use.  Some integrate the apps with their own software making for a more unified output.  What I am doing is research as to what presentation I like the best for my application.  Gotta use it to find that out, and don't want huge investment in hardware.

---

