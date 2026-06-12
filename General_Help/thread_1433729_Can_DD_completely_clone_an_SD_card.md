---
title: "Can DD completely clone an SD card?"
date: 2010-03-19
forum: General Help
---

### Post by zerowun on 2010-03-19
I have come across an issue when cloning an SD card.

I have a SheevaPlug, which is a low power ARM based computer.  I used an Intel based HP laptop running Ubuntu 9.04 to clone the 4GB SD card of the SheevaPlug.  The card contains 2 partitions: the boot image, and the root filesystem.  I did this using dd directly from one 4GB card to a second 4GB card (sudo dd if=/dev/sdb of=/dev/sdc), and also by dumping the first card to an image file and then from the image file to the second card.  The process worked successfully in that the SheevaPlug seems to run fine off the cloned card, but here’s the strange thing: when I use Gparted to examine the original card, it shows it has 2 partitions.  However, when I do the same with the cloned card, Gparted detects no partitions at all.  Ubuntu seems to mount the partitions fine as well.  Anyone have any idea what might be happening?  I thought DD was supposed to perform a bit-for-bit copy of the whole device given the parameters I used, and that Gparted should therefore show identical results no matter which card it was looking at. I unmounted the cards before running DD by the way.

---

### Post by 2hot6ft2 on 2010-03-19
Looks like you're not the first to do it. Might take a look at this thread which was quickly found with google:
[How to clone a SheevaPlug?]("http://plugcomputer.org/plugforum/index.php?topic=1317.0")

[Learn the dd command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")
For more on using dd.

---

### Post by zerowun on 2010-03-19
That doesn't address the issue I raised, i.e. why isn't dd making a bit-for-bit copy of the SD card.

---

### Post by 2hot6ft2 on 2010-03-19
> **zerowun said:**
> The process worked successfully in that the SheevaPlug seems to run fine off the cloned card
So dd did make a data dump to the second card successfully.
> **zerowun said:**
> but here&#8217;s the strange thing: when I use Gparted to examine the original card, it shows it has 2 partitions.  However, when I do the same with the cloned card, Gparted detects no partitions at all.  Ubuntu seems to mount the partitions fine as well.
Sounds like the issue is more with GParted than with dd. I have had GParted not show my hard drive before so since it's obviously there I think it's a bug in GParted.

You're right it **should** show the same info as the first card and I don't know why it doesn't. Still it looks like dd did what it was supposed to.

[Search results for GParted not showing drive]("http://www.google.com/search?q=gparted+not+showing+drive&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")
and
[gparted not showing partitions]("http://www.google.com/search?hl=en&client=firefox-a&hs=SSg&rls=com.ubuntu%3Aen-US%3Aofficial&q=gparted+not+showing+partitions&aq=f&aqi=&aql=&oq=&gs_rfai=")

---

### Post by zerowun on 2010-03-19
The problem with that hypothesis is that Gparted behaves consistently with both SD cards no matter what (e.g. rebooting, swapping the hardware devices I use to mount the SD cards, etc).  The only logical conclusion I can draw is that the 2 cards have not been cloned absolutely identically, so the question is: what is dd **not **copying?

---

### Post by solitaire on 2010-03-19
Have you tried running "testdisk" on the cloned card?
It might let you know if dd is not copying everything or if it's a problem with gparted.

It's in the repos. find out more about it and how to use it:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by ubunterooster on 2010-03-19
No offense intendid but I prefer Clonezilla. You can specify to copy partitions OR entire drives, bit-by-bit. I've yet to have a problem with it.

---

### Post by srs5694 on 2010-03-19
A couple of comments/ideas:

First, I've been seeing a lot of posts lately from people who report that GParted is showing their disks as empty even when other tools show them to have partitions. It's possible that there's a bug in at least some versions of GParted that's causing it to misbehave. Note that this bug could theoretically be interacting with something else about the two SD cards, such as their *exact* size, to cause this problem.

Second, do you know what type of partition table the SD card uses (MBR, GPT, or something else)? Although MBR data appear entirely at the beginning of the disk (or interspersed with the logical partitions, in the case of logical partitions), GPT includes both a main partition table at the start of the disk and a backup partition table at the end of the disk. If you use dd to make a byte-for-byte identical clone of one GPT disk onto another disk, the backup table will be in the wrong location, or perhaps won't be present at all, if the two disks aren't exactly the same size. I don't honestly know how GParted handles this situation. It's certainly conceivable that it would respond by reporting that the disk is empty, but I'd like to emphasize that I don't know this for a fact; it's just a possibility I'm tossing out. There could be similar issues with some other more exotic partition table formats.

---

### Post by dcstar on 2010-03-19
> **srs5694 said:**
> A couple of comments/ideas:
.......

Possibly SD cards can have certain data areas that are just not available for access by software devices that treat them as traditional drives.

I know SSD devices can themselves remap the internal storage areas to rotate wear, and the external interface knows nothing of this as it uses the "logical" locations which may not always correspond to the physical locations.

If the second SD card has space right at the start of the storage area that is never actually written to, then Gparted might be looking at that area assuming data it wants will be there, while other programs may not bother and they still work ok.

I have seen things like this with old USB drives - but not for a while now.

---

### Post by asmoore82 on 2010-03-19
try running this commands back to back with both of the cards plugged in...
They are both non-destructive, just reporting drive geometry:
```
sudo sfdisk -g
sudo sfdisk -G
```

I would bet that you'll uncover an inconsistency there that is fooling gparted.

It's quite common though and as you have demonstrated has no effect on the usability of the cards.
Even as I type this I have a 512MB SD card in my laptop now that is not consistent:
```
[COLOR="Red"]**~$** sudo sfdisk -g /dev/mmcblk0[/COLOR]
[COLOR="Purple"]/dev/mmcblk0: 15484 cylinders, 4 heads, 16 sectors/track[/COLOR]
[COLOR="Red"]**~$** sudo sfdisk -G /dev/mmcblk0[/COLOR]
[COLOR="Purple"]/dev/mmcblk0: 61 cylinders, 255 heads, 63 sectors/track[/COLOR]
```

---

### Post by dcstar on 2010-03-20
> **asmoore82 said:**
> try running this commands back to back with both of the cards plugged in...
They are both non-destructive, just reporting drive geometry:
```
sudo sfdisk -g
sudo sfdisk -G
```

I would bet that you'll uncover an inconsistency there that is fooling gparted.

It's quite common though and as you have demonstrated has no effect on the usability of the cards.
Even as I type this I have a 512MB SD card in my laptop now that is not consistent:
```
[COLOR="Red"]**~$** sudo sfdisk -g /dev/mmcblk0[/COLOR]
[COLOR="Purple"]/dev/mmcblk0: 15484 cylinders, 4 heads, 16 sectors/track[/COLOR]
[COLOR="Red"]**~$** sudo sfdisk -G /dev/mmcblk0[/COLOR]
[COLOR="Purple"]/dev/mmcblk0: 61 cylinders, 255 heads, 63 sectors/track[/COLOR]
```
If the two different SD cards have different pseudo physical characteristics, then that could be the issue as the dd will copy the wrong logical partition table setup to the other SD card.

---

### Post by HermanAB on 2010-03-20
Hmm, it looks like you copied the partition and not the whole device.  So your dd if= parameter was wrong.

---

### Post by zerowun on 2010-03-20
Thanks [COLOR=Blue]dcstar[/COLOR].  I am fairly new to Unix and didn’t know about sfdisk.  Running that revealed some interesting information:

[LIST]
[*]using the –g & -G options showed that both cards had 4 heads and 16 sectors per track, but the original card had 124,928 cylinders, while the target card had only 122,176 cylinders
[*]using the –l option showed that the partition tables were identical
[*]however, the –V option warned that partition 2 of the target card extended past the end of the card.  I guess this is the reason that Gparted had a problem with it.
[/LIST]
   Out of curiosity, I looked at a third 4GB card I use.  That also had a different number of cylinders - 122,560.

I think the lessons I’ve learned from this are:

[LIST]
[*]flash cards vary in size; e.g. if a card is specified as being 4GB, the only thing you can assume is that it has 4,000,000,000 bytes and may have considerably more
[*] if you are trying to clone a card, make sure that either the target card is large enough, or shrink the partitions on the source card to make sure they will fit.
[/LIST]
 Thanks for all your help.:D

---

### Post by dcstar on 2010-03-20
> **zerowun said:**
> Thanks [COLOR=Blue]dcstar[/COLOR].  I am fairly new to Unix and didn’t know about sfdisk.  Running that revealed some interesting information:

[LIST]
[*]using the –g & -G options showed that both cards had 4 heads and 16 sectors per track, but the original card had 124,928 cylinders, while the target card had only 122,176 cylinders
[*]using the –l option showed that the partition tables were identical
[*]however, the –V option warned that partition 2 of the target card extended past the end of the card.  I guess this is the reason that Gparted had a problem with it.
[/LIST]
   Out of curiosity, I looked at a third 4GB card I use.  That also had a different number of cylinders - 122,560.

I think the lessons I’ve learned from this are:

[LIST]
[*]flash cards vary in size; e.g. if a card is specified as being 4GB, the only thing you can assume is that it has 4,000,000,000 bytes and may have considerably more
[*] if you are trying to clone a card, make sure that either the target card is large enough, or shrink the partitions on the source card to make sure they will fit.
[/LIST]
 Thanks for all your help.:D

You can also use Gparted to copy individual partitions from one device to another - that way things are done correctly as the partition is added in as per normal to the partition table. The only issue is that you don't copy the boot sector.

---

### Post by zerowun on 2010-03-21
Thanks.  I did that when I copied both partitions on the original 4GB card to an 8GB card.  I then grew the second partition - also using Gparted - into the unallocated space on the 8GB card. That went without a hitch.

---

