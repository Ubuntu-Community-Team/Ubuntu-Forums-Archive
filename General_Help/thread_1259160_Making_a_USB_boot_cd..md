---
title: "Making a USB boot cd."
date: 2009-09-06
forum: General Help
---

### Post by tony v on 2009-09-06
I am new to ubuntu and am floundering badly. I need some help please.
The only place available to me to install ubuntu 9.04. is my huge external hard drive.
So that's what I have done.
Now I need to be able to boot to this new installation.
 
I have tried to follow the instructions as outlined in 'Booting the kernal from a bootable CD.' 
Prepare your bootable CD.........etc.... 
This in turn is on line under Ubuntu Documentation. "Ubuntu Documentation >Community Documentation>BootFromUSB"
 
My computer cannot boot a USB device from BIOS. Which is why I need a bootable CD.
 
The first area that I strike trouble is as follows:
mkdir -p iso/grub (No problem so far)
 
Copy initrd and vmlinuz to the boot folder:
cp /cdrom/casper/initrd.gz iso/boot 
(I get the message ' cp: cannot stat.... This file does not exist.)
 
I suspect that the instruction I am trying to follow is out of date or I am not doing something correctly. Hope someone can put me on the right track. 
Kind Regards: tony v

---

### Post by skalra63 on 2009-09-06
i had the same issue when trying to create the boot cd from an installation. I had to create it from a live cd session.

but then again, mine doesnt actually boot

---

### Post by darsu on 2009-09-06
(edited - sorry, my question was redundant)

---

### Post by makariolewis on 2009-09-06
I'm not quite sure I understand your question completely. To me, it sounds as if you want to install Ubuntu to your external hard drive using a boot CD, but you want your computer to be able to boot from that external hard drive.

If that's the case, it should be relatively simple. Just go to [www.ubuntu.com/download](www.ubuntu.com/download) and download the .iso file. Then, burn it to a disc. (If you're using Ubuntu already, burning an .iso to a disc is as simple as right-clicking and choosing "Write to Disc.."; if you're on Windows, you can read how to burn an iso [here]("https://help.ubuntu.com/community/BurningIsoHowto#Windows").)

Once you've burned your CD, just boot to it from your computer and install Ubuntu to your external hard drive. The installation process will (should) automatically prepare GRUB (which tells your computer what OS to boot) for booting from your external harddrive. That's about it.

Hope this answers your question.

---

### Post by tony v on 2009-09-07
Thanks for your input mackariolewis.  Please bear in mind that I have never touched linux till now.
I have already installed ubuntu 9.04 to my external USB hard drive. I just need to be able to access it. ie boot to it from my computer. Its just sitting there loafing at the moment and I can't get to it. I can only use 9.04 from my live disc at present. I need to be able to make a boot c.d. that contains Grub (I think) that will boot to my new installation. I have been trying to make this c.d. using the information posted on line. This info may be old.
tony v

---

