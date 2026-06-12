---
title: "UNR vs Ubuntu on a Celeron EeePC"
date: 2010-11-21
forum: General Help
---

### Post by Fallingwater on 2010-11-21
I have an old EeePC 701 4G, with a Celeron 900 processor (re-clocked to  its standard 900MHz speed via BIOS patch; the stock 701 underclocks it  to 633). I'm giving it to a fairly computer-illiterate friend who needs  it to see PDF files and occasionally go online, so I installed Ubuntu  Netbook 10.4 and configured it and installed stuff and all that. And  then I found out that Ubuntu Netbook is optimized for Atoms, and suffers  a performance hit on Celerons.

What sort of performance hit are we talking about here?

Because I'm half tempted to wipe everything and install standard Ubuntu  and the UNR interface (package netbook-launcher) on top of it, but I'll  spare myself the work if the performance difference is only a few  percent.

Thanks.

---

### Post by Artemis3 on 2010-11-21
I use that machine at the stock 630mhz speed and Unity (10.10) works very fine, simply because of the intel video gma9xx which is well supported. (The older UNR also worked fine for the same reason).

My only suggestion, leave it underclocked, it will run cooler. You never know where your friend might end up using this. Reading pdfs and doing online browsing doesn't really need more.

Mine has 2g or ram which helped with Gnome, if yours is still 512m, you might want to explore either Xubuntu or Lubuntu instead. I suggest you format a single ext2 partition; no swap, no journaling fs, (could be ext4 with journaling turned off), oh and the noatime in fstab is a must :).

---

### Post by Fallingwater on 2010-11-21
I tried 10.10 with Unity and it was a nightmare. I much prefer 10.04's much faster interface, and since that's the LTS I don't really see much reason to upgrade. It does still have the original half-gig of RAM; I never upgraded it because I quickly got tired of the tiny screen and replaced the netbook with a 1005HA. If I ever upgrade that one's RAM to two gigs I'll put its 1G module in the 701, but for the moment the current module is staying.

Anyway, I've had a bit of a fight with the friend in question yesterday, so I'm keeping the 701 for myself. I still need to know what's the performance hit with UNR's Atom optimization...

---

### Post by Fallingwater on 2010-11-22
I ran the hardinfo CPU tests in UNR, then I ran Ubuntu live from a thumbdrive and repeated them. The results were close enough as to make no difference (if you want to nitpick, all tests were about one percent point faster **on UNR**, but I ascribe this result on the phase of the moon). 

Based on this test, I'm fairly sure whatever optimization UNR has for the Atom is merely disabled when running on the Celeron - it doesn't hinder its performance at all. 

And I don't have to reinstall the system. :)

---

### Post by snowpine on 2010-11-22
Ubuntu has not had a separate "Atom optimized" release since 2009, and Ubuntu has "Tier 1" support for the ASUS EEE 701, according to this page: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20701)

---

