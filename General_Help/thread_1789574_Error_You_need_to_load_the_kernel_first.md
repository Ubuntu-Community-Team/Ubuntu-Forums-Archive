---
title: "Error: You need to load the kernel first"
date: 2011-06-24
forum: General Help
---

### Post by Koha23 on 2011-06-24
I just installed Ubuntu 11.04 onto a partition and am dual-booting it with Windows 7. I got to the install for Ubuntu where it extracts the language packs and things like that and it has the "Slideshow" where it shows you all the new features, I got past that and restarted my computer. But when I start from GRUB it it goes into a command prompt type thing (Sorry, I'm used to windows) and it says "Error: You need to load the kernel first". I've looked around on Google and seen quite a few articles about it but it was all for 9.10 not 11.04. Please help.

---

### Post by wildmanne39 on 2011-06-24
> **Koha23 said:**
> I just installed Ubuntu 11.04 onto a partition and am dual-booting it with Windows 7. I got to the install for Ubuntu where it extracts the language packs and things like that and it has the "Slideshow" where it shows you all the new features, I got past that and restarted my computer. But when I start from GRUB it it goes into a command prompt type thing (Sorry, I'm used to windows) and it says "Error: You need to load the kernel first". I've looked around on Google and seen quite a few articles about it but it was all for 9.10 not 11.04. Please help.Hi, can you still boot windows? You will need to run this script from a terminal from the livecd and post the information from this script so we can see where everything is located:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Koha23 on 2011-06-24
I don't have a liveCD. I'm using Wubi. I'm sorry, I really am I'm so new at this I don't know a thing that I'm doing other than to make a new partition, use Wubi to install Ubuntu to the partition and supposedly work. Is there anyway you could do or find like a complete step by step hold your hand kind of tutorial for my feeble mind? I've looked all over Google and Bing both and couldn't find a thing

---

### Post by wildmanne39 on 2011-06-24
Hi, I am going to give you a link for wubi.
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Rubi1200 on 2011-06-24
Hi Koha23,
when you get to the grub> prompt type the following commands and tell us what the output shows:
```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```

Afterwards, type "reboot" to start the computer again and go to Windows.

On Windows, look for the following files at the root of the drive where you installed Wubi:
wubildr
wubildr.mbr

Confirm if the files are there.

Also check the /ubuntu folder and look for a folder labeled /disks and check if the root.disk is there.

---

