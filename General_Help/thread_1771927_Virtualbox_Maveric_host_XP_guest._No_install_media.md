---
title: "Virtualbox Maveric host XP guest. No install media"
date: 2011-05-30
forum: General Help
---

### Post by sea_dawg on 2011-05-30
If I understand the process of getting Win XP running under virtual box I need a Win XP installation CD.  Unfortunately both my desktop and laptop came with Windows recovery partitions rather than installation CDs.  I have been unable to create Windows installation CDs.  I am able to create recovery CDs, but they are not seen by Virtualbox as bootable media.

This leads me to my questions:

1 - Does anyone know how to create Windows XP installation CDs from the recovery partition on Gateway desktops and Lenovo laptops?

failing that:

2 - Is it possible to create and ISO of the existing Windows installation using something like imgBurn and then load that ISO into Virtualbox?

or:

3 - Is it possible to use something like Clonezilla to clone the existing Windows installation onto the Virtualbox "hard disk"?  I'm guessing this one is going to take quite a lot of space

or, more than likely

4 - Am I barking up the wrong tree and need to rethink the whole process?

Desktop
Gateway 507GR (vintage late 2004 early 2005)
P4
4 GiB ram
Original 190 GiB HDD with Win XP
Additional 500 GiB HDD with Ubuntu 10.10

Laptop
Lenovo R61 (2006? 2007)
Intel Core 2
2 GiB ram
120 GiB HDD with both Win XP and Ubuntu

---

### Post by Mark Phelps on 2011-05-31
Sorry ... but AFAIK, the answer to the first three questions is NO ... and the answer to the fourth is YES.

You will need to get hold of XP Installation media somehow.

---

### Post by linuxinstalledfromhdd on 2011-05-31
Buy one from Ebay for 15. 

Don't download it illegally, whatever you do.

> **sea_dawg said:**
> If I understand the process of getting Win XP running under virtual box I need a Win XP installation CD.  Unfortunately both my desktop and laptop came with Windows recovery partitions rather than installation CDs.  I have been unable to create Windows installation CDs.  I am able to create recovery CDs, but they are not seen by Virtualbox as bootable media.

This leads me to my questions:

1 - Does anyone know how to create Windows XP installation CDs from the recovery partition on Gateway desktops and Lenovo laptops?

failing that:

2 - Is it possible to create and ISO of the existing Windows installation using something like imgBurn and then load that ISO into Virtualbox?

or:

3 - Is it possible to use something like Clonezilla to clone the existing Windows installation onto the Virtualbox "hard disk"?  I'm guessing this one is going to take quite a lot of space

or, more than likely

4 - Am I barking up the wrong tree and need to rethink the whole process?

Desktop
Gateway 507GR (vintage late 2004 early 2005)
P4
4 GiB ram
Original 190 GiB HDD with Win XP
Additional 500 GiB HDD with Ubuntu 10.10

Laptop
Lenovo R61 (2006? 2007)
Intel Core 2
2 GiB ram
120 GiB HDD with both Win XP and Ubuntu

---

### Post by sea_dawg on 2011-05-31
Thank you both for your replies.  linuxinstalledfromhdd, I agree, no illegal downloads.  

I do find it ironic that I am the owner of fully licensed copies of XP for the machines I wish to install XP into Virtualbox, yet I have to purchase additional copies.

Yet another reason to love open source.

---

### Post by pricetech on 2011-05-31
But you'll need a third license for the instance of XP running under VirtualBox.

For future reference, don't buy a computer that doesn't come with install media.

---

