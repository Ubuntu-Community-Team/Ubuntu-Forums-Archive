---
title: "Retrieving old Windows XP installation"
date: 2011-09-15
forum: General Help
---

### Post by pzs on 2011-09-15
My newish home box is a Linux machine but I would like to have Windows for Games and other bits. 

On my previous machine I had a main Windows XP drive (an IDE drive) with GRUB on it that pointed to a second drive with Linux. I'd like to try and wire that old Windows XP drive into my new machine and get it to boot. I've already done the hardware stuff and I can read the drive - the contents look fine. Is it possible to retrieve it as a bootable OS?

Here are the problems:

- The old drive has GRUB on the boot block. I guess I have to remove this so that I can just boot from the drive plain. How do I do this?

- My memory is that Windows did not play nice if it was not the main drive, and if you wanted Linux and Windows together Windows always had to be the main drive. Is this still true of Windows XP? 

- Will I also have problems because my main drive is now a SATA drive and I want the GRUB installation to point at an IDE drive?

- I'm not even sure if the licensing will work - will Windows XP spot that it's on a different machine and fail?

If this will be impossible, I could also try reinstalling Windows XP on the old drive - I still have media and key. Will this be quicker? Or will I still have problems with Windows being on the non-main drive?

Thanks for any expert guidance!

Peter

---

### Post by Frogs Hair on 2011-09-15
I think you could update grub , but windows is only legal on the computer it is first installed on . Though I have a Win 7 disc it can't be used for installation on another computer . The system information on the hard-drive would not match the other computer .

---

### Post by MARP1961 on 2011-09-16
Even if you manage to get Windows XP back on, it will detect that the motherboard is different and therefore is not the original computer. You will not be able to 'activate' Windows and the install will only work for 30 days. 

You will need to buy a new Windows license. If your computer is modern specification then Windows 7 would make more sense.

---

