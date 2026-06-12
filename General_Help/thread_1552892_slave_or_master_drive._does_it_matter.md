---
title: "slave or master drive. does it matter?"
date: 2010-08-14
forum: General Help
---

### Post by princeofnam on 2010-08-14
i'm about to perform a fresh ubuntu install, and i was wondering if anyone knew whether installing on the slave or master drive mattered.



i know if you're installing on the same drives it's slightly faster for ubuntu to be installed first, but that doesn't seem to be the case since i have two separate drives

---

### Post by TyLLy_4 on 2010-08-14
Operating systems have to go on the master drive as its the only one that will boot. 

U cannot install in a salve drive.

---

### Post by philinux on 2010-08-14
princeofnam,

I have two internal hard drives with lucid on one and maverick on the other. Both boot fine.

Whats on your drives currently.

Windows likes to be on the first drive or it complains IIRC.

---

### Post by TyLLy_4 on 2010-08-14
Sorry. Some quick goggling shows me that you can indeed boot from a slave drive. 


My post above was based on my Microsoft certification classes where they tech us that you can only install windows on the Master C: Drive. 


Luckily we don't have such limitations on Ubuntu. 


Also, be sure to make a partition for your /home folder when you install. This way if things go wrong you wont loose your settings or data.

Sorry about the misinformation.

---

### Post by princeofnam on 2010-08-14
no problem. will ubuntu boot or operate any slower for being on the slave drive?

---

### Post by princeofnam on 2010-08-14
there's also a lot of advice about having to unplug and replug hdds while setting up dual boots. not sure if any of that is true

---

### Post by philinux on 2010-08-17
> **princeofnam said:**
> no problem. will ubuntu boot or operate any slower for being on the slave drive?

No.

---

### Post by philinux on 2010-08-17
> **princeofnam said:**
> there's also a lot of advice about having to unplug and replug hdds while setting up dual boots. not sure if any of that is true

I've been dual booting 2 internal HD's for 3 years. Never had to unplug one.

---

### Post by QLee on 2010-08-17
> **philinux said:**
> I've been dual booting 2 internal HD's for 3 years. Never had to unplug one.

+1 (with 3 internals, both master & slave drives, for more than 5 years)

However, yes, there are competent users here who recommend the separate drive and separate MBR approach and who then use BIOS settings to choose boot drive. It is an opinion and a "style", people choose what works best for them. There is nothing wrong with either method for someone who knows how GRUB (and these days GRUB2) works. For someone who doesn't understand, either method can present difficulties. I think the "best" method depends on the specific situation and user. In the case of a removable drive, some faillsafe method of booting when the drive is unplugged has to be considered.

---

### Post by Nervouswreck on 2010-08-17
Pardon my ignorance, but why would anyone want to unplug a drive during installation?? Strikes me as a way to ruin a good hd??

Also:
It is possible to boot Windows 2000 from a slave drive using Dell's BIOS revision A03. (seen it. Don't know how it was done.)

---

### Post by TyLLy_4 on 2010-08-17
Im not sure ... but it goes ageist everything we learned in Microsoft certification class .... (and i love it)

---

