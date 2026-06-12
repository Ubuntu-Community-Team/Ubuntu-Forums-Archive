---
title: "Swapping motherboards... do I have to reinstall?"
date: 2009-09-20
forum: General Help
---

### Post by heartburnkid on 2009-09-20
I'm going to be swapping the motherboard in my HTPC soon... I know that when using Windows, it's pretty much a necessity to do a reinstall when going to a different motherboard.  How about with Ubuntu?  Can I keep chugging along with my current install until 9.10 goes gold, or will I need to reinstall with the new mobo?

If it matters for the question, the current motherboard is a Socket 939 nForce 430-based board, and the replacement is a Socket AM2+ AMD 785G-based board.

---

### Post by TransitMan on 2009-09-20
I did a motherboard swap and Ubuntu just chugged right along.
YMMV but it all comes down to when you fire it up the first time if anything "breaks", then it will be command line and "sudo apt-get upgrade" to get the latest whatever you might need.
Good luck.

---

### Post by elliotn on 2009-09-20
i changed mobos n ubuntu jst worked.

---

### Post by blackened on 2009-09-20
Backup everything you want to save and swap the mobo. Best case scenario, it works, worst case scenario, it doesn't and you do a clean install.

---

### Post by odinb on 2009-09-20
If you stay with the same GPU (i.e you use nVidia on both MoBos), it should just be a clean swap. If you also change the GPU, uninstall the proprietary drivers first, and it should be smooth sailing after that.

Then you ofcourse install the proprietary drivers for your GPU on the new MoBo.

Good luck!

P.S. if you have any other proprietary drivers installed, i.e. for WLAN, and your WLAN also changes, it might be a good idea to uninstall those also before the swap.

---

### Post by darco on 2009-09-20
I always heard if its the same CHIPSET, then you are good to go...

darco

---

### Post by 3rdalbum on 2009-09-20
Make sure you plug the SATA cables into the same numbers; for instance, if your hard disk is currently plugged into the header marked "SATA_1", make sure it's plugged into "SATA_1" on the new motherboard.

Otherwise, you would need to reinstall GRUB.

Also, remove all proprietary drivers that are specific to the old motherboard.

---

### Post by pcjunkie on 2009-09-20
No don't reinstall Grub -

Just change the BIOS order and test..
2 hard drives gives you a 50/50 chance..:P

---

