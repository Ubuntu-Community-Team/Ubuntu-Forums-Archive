---
title: "Karmic vs Jaunty mounting HD1"
date: 2010-01-30
forum: General Help
---

### Post by n.hinton on 2010-01-30
Everything works fine this is just an aesthetic irritation, mounting HD1 (windows vfat HD) in jaunty, no problem, but with karmic!!! please see screenshots, think karmic is displaying hex of  volume serial number.

As I said everything works as it should, but it would be good if I could get karmic to behave like jaunty.

Any advice much appreciated.

---

### Post by dcstar on 2010-01-30
> **n.hinton said:**
> Everything works fine this is just an aesthetic irritation, mounting HD1 (windows vfat HD) in jaunty, no problem, but with karmic!!! please see screenshots, think karmic is displaying hex of  volume serial number.

As I said everything works as it should, but it would be good if I could get karmic to behave like jaunty.

Any advice much appreciated.

Different Ubuntu releases use different Gnome releases, the key word is that they are **different**.

---

### Post by n.hinton on 2010-01-30
> **dcstar said:**
> Different Ubuntu releases use different Gnome releases, the key word is that they are **different**.

Yes different may be a keyword and so could be 'regression', however, keywords had nothing to do with my post.

Advice on the issue would be much appreciated.

---

### Post by louieb on 2010-01-30
Fire up a live CD - open Gparted - right click on the partition - select label - give it a name. Will show up forevermore with that name.

---

### Post by gradinaruvasile on 2010-01-30
More simple solution:

Open the Disk Utility (in the administration menu), unmount the partition, give it a label (name) and mount it back.

---

### Post by n.hinton on 2010-01-30
Many thanks for your reply's louieb and gradinaruvasile but had already done both sugestions before making post 1. 

Live Gparted reported sucsessfull operation but after it finished refreshing returned to the identicle label. 

Disk Utility, twice asked for autherisation passwords, which I typed in then failed due to 'Not Authorised' (yes I do know my password).

Many thanks guys

PS It is the VFat volume serial number that karmic displaying the hex of.

---

### Post by n.hinton on 2010-01-30
To provide a little background:

I had a dual boot HD with Karmic (upgraded from jaunty) along with the original Vfat windows primary partition.

I installed a new hard drive as primary master and used live gparted to copy my linux partitions to the new HD and delete said partitions on old disk, then re-grow primary VFat to fill HD, added: map (hd0) (hd1), map (hd1) (hd0), after chainloader +1, to menu.lst, so as to be able to boot the windows partition.

The second screenshot (karmic) is from my installed karmic, the jaunty screenshot is from a 'try ubuntu' jaunty CD, I thought it maybe my karmic installation at fault, so booted karmic from distro CD  and behaviour exactly the same as my installed karmic.

Doubt if the above is relevant, but posting just in-case.

---

### Post by louieb on 2010-01-31
Haven't used vfat since I gave up floppies and WIN98 so can't test it but according to the [Gparted Features Page]("http://gparted.sourceforge.net/features.php")  to assign a label to a vfat partition you need **dosfstools and mtools** installed too.

---

### Post by n.hinton on 2010-01-31
> **louieb said:**
> Haven't used vfat since I gave up floppies and WIN98 so can't test it but according to the [Gparted Features Page]("http://gparted.sourceforge.net/features.php")  to assign a label to a vfat partition you need **dosfstools and mtools** installed too.

Hi louieb, thanks for your reply.

I have **dosfstools and mtools** installed and had labelled HD1 that way also e.g. 
```
sudo mlabel -i /dev/sdb1 ::HD1
kingfisher@kingfisher-desktop:~$
kingfisher@kingfisher-desktop:~$ sudo mlabel -i /dev/sdb1 -s ::
Volume label is HD1
```
But this makes no difference to karmic, jaunty displays HD1 correctly with or without partition label.

Thanks for your input though

---

