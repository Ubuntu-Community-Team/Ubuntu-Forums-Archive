---
title: "Odd problem.  No grub.cfg file, can't create one"
date: 2012-05-06
forum: General Help
---

### Post by bobnutfield on 2012-05-06
Hello Everyone

I have an old net book (Acer Aspire One, 2008) that I still use from time to time.  I originally installed Jaunty on it, and have continuously upgraded all the way to 12.04. I have never experienced any problems until now.  Yesterday, there were a large number of updates, and it included a kernel updat (3.2.0, I believe.  Everything seemed to go fine, but when I rebooted, I found that I was still running the kernel from 11.10 (3.0.0) and several apps would not open.  After investigating, I discovered that there is no grub.cfg file, so the system is booting from an old menu.lst file.  I ran update-grub, which found the new kernel, but would not create a cfg file.  I cannot halt the boot to look at the menu (holding down the shift key).

Anyone know how I can create a grub.cfg file to fix this?  Right now, the lack. Of one is causing grub to use the old menu.lst file.

Any help appreciated.

---

### Post by wilee-nilee on 2012-05-06
Easy fix we can remove grub legacy and install grub2 in the terminal run these commands and when asked where grub goes it is the mbr not a partition, the mbr is sda "probably" no numbers. 

```
sudo apt-get purge grub grub-pc grub-common
```Then

```
sudo apt-get install grub-pc grub common
```After all is done run.

```
sudo update-grub
```

It helps to know this as well when you get to the choice of where grub goes you use the space key to tick it.

---

### Post by bobnutfield on 2012-05-06
Thank you, wilee, that worked like a charm.  It did indeed create the file I needed to boot properly into the right kernel.  However, it left the legacy grub installation installed.  It, did, however give me the command to upgrade completely from legacy grub:

> upgrade-from-grub-legacy

That seemed to reinstall everything correctly.

All is good now.

Thank you for your help.  I'm surprised, but this old netbook still handles full blown Ubuntu as well as my dual core laptop.

---

### Post by wilee-nilee on 2012-05-06
> **bobnutfield said:**
> Thank you, wilee, that worked like a charm.  It did indeed create the file I needed to boot properly into the right kernel.  However, it left the legacy grub installation installed.  It, did, however give me the command to upgrade completely from legacy grub:



That seemed to reinstall everything correctly.

All is good now.

Thank you for your help.  I'm surprised, but this old netbook still handles full blown Ubuntu as well as my dual core laptop.

Your welcome, I have a aspireone d250 with 2 gigs ram it runs Ubuntu like a champ and W7 as well. It is the backup as of now I bought a little older dual core toshibe laptop it runs faster with the chip set. Darn Toshiba though is a big heavy lug in comparison.

---

### Post by bobnutfield on 2012-05-06
Yes, it's hard for my old eyes to see, but this one is the old N270 with only a gig of ram and 120gb disk.  Much faster and smoother that either of my two dual core laptops.  Just wish I could see it!!

---

### Post by wilee-nilee on 2012-05-06
> **bobnutfield said:**
> Yes, it's hard for my old eyes to see, but this one is the old N270 with only a gig of ram and 120gb disk.  Much faster and smoother that either of my two dual core laptops.  Just wish I could see it!!

I forgot about the auto upgrade and that it might still be in the cue to finish. I updated to grub 2 even before jaunty it has been awhile. I figured the purge would just clean it all out, I'm not sure where that prompt is after a purge.

I have to use reading glasses with that acer on the road but at home I have a older flat screen and used the acer as a tower with a keyboard basically.

---

### Post by bobnutfield on 2012-05-06
My Acer is just used to store documents and photos now.  Used to be my constant travel companion with a mobile broadband stick.  Now I have an Ipad to carry around, easier but not nearly as versitle as the old netbook was.  Never bothered to jailbreak the Ipad, so I can't network with it, but it is great for mobile internet.

---

