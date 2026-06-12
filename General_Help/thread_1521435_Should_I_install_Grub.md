---
title: "Should I install Grub"
date: 2010-06-30
forum: General Help
---

### Post by clayman1000x on 2010-06-30
Now that I have Ubuntu up and running should I install grub or not? I am at that stage in update manger process and don't know what to do. Ubuntu is to dual boot with XP, do I want Grub?

---

### Post by wilee-nilee on 2010-06-30
Is this a wubi or straight separate partitions dual boot?

If you have booted from the cd and it is separate partitions you would put grub in the MBR for example sda no numbers.

---

### Post by clayman1000x on 2010-06-30
> **wilee-nilee said:**
> Is this a wubi or straight separate partitions dual boot?

If you have booted from the cd and it is separate partitions you would put grub in the MBR for example sda no numbers.
I think it is a Wubi, it is installed inside windows.

---

### Post by wilee-nilee on 2010-06-30
> **clayman1000x said:**
> I think it is a Wubi, it is installed inside windows.

Then no don't accept the grub install, hit n.

---

### Post by techunit on 2010-06-30
Where are you getting asked this question for yes or no.

---

### Post by wilee-nilee on 2010-06-30
> **techunit said:**
> Where are you getting asked this question for yes or no.

I think it's a update, the stock grub that is part of the wubi install should work fine and any addition may put in the mbr or the windows partition.

---

### Post by clayman1000x on 2010-06-30
All good, solved. Thank you very much for your quick answers.

---

### Post by wilee-nilee on 2010-06-30
> **clayman1000x said:**
> All good, solved. Thank you very much for your quick answers.

Just remember that this type of install is really a tryout setup to eventually have a real dualboot, so the OS doesn't know it is inside of Windows, so at times you may get updates like a grub one that will bork it and need repairs. If you want to dual boot eventually here is a link in case you need some help.
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

---

