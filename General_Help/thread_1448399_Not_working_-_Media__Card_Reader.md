---
title: "Not working - Media  Card Reader"
date: 2010-04-06
forum: General Help
---

### Post by lnavarrete on 2010-04-06
I have a Gateway LT2104u with an integrated Multi-in-1 card reader. ubuntu netbook remix doesn't "see" it. There is nothing I can find in the OS that can help me access the media card. Disk Utility doesn't show it and Volumes under Files & Folders is empty.
Hope someone has an answer. Thank you.

---

### Post by killerrich on 2010-04-19
I also have a Gateway LT2104u netbook, but I'm running 9.10 standard, and I've had no luck with my card-reader either. There doesn't seem to be a lot of other people running this particular model on this forum, as there was no response from the "gurus" on another issue I and a few other people were having with the wireless adapter. Maybe they have a bias against Gateway machines, which is understandable, but these are just a re-badged Acer anyway. I'll keep fishing around the forums, (other makes/models may use the the same reader, so it's maybe better to search for the specific reader), and post here again if I have any luck.

---

### Post by eddieamp on 2010-06-06
Same issue here. Running Ubuntu Netbook Edition 10.04 on a Gateway LT2104u. The MMC card reader doesn't show up in lspci. I've tried modprobeing in sdhci from the [Gentoo Wiki]("http://en.gentoo-wiki.com/wiki/SD_and_MMC_card_readers"), but no dice. Fresh out of ideas.

---

### Post by devildogmech on 2010-10-01
Bueler? bueler? 

Same problem.....

---

### Post by avacado on 2010-10-14
try $ lsusb
if you have the 0cf2:6250 ENE technology then same card reader as me.

If so please subscribe to my bug and add weight to the problem.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)

It may take some time for a volunteer developer to write the driver.
In the mean time use an external card reader or camera to read\write to card.

---

