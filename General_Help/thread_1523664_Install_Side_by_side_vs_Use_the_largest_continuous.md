---
title: "Install Side by side vs Use the largest continuous space"
date: 2010-07-04
forum: General Help
---

### Post by COKEDUDE on 2010-07-04
When trying to set up a dual boot is it better to use Install Side by side or Use the largest continuous space? Would using the largest continuous space cause problems with grub or delete the other partition?

[IMG]http://lookpic.com/d2/i2/353/TvCwMzwt.png[/IMG]
[http://lookpic.com/d2/i2/353/TvCwMzwt.png](http://lookpic.com/d2/i2/353/TvCwMzwt.png)

---

### Post by hansdown on 2010-07-04
Hi COKEDUDE.

Install side by side will take care of everything.

---

### Post by wilee-nilee on 2010-07-04
With any MS partition resizing your best to do it after defragging it first. Then with XP you can use gparted but reboot it to make sure it's okay then install Linux. Your better still having the XP bootloader in the mbr if there is a problem.

---

### Post by COKEDUDE on 2010-07-04
> **hansdown said:**
> Hi COKEDUDE.

Install side by side will take care of everything.

Whats the Use the largest continuous space option for? Would installing side by side also install a swap partition? 

> **wilee-nilee said:**
> With any MS partition resizing your best to do it after defragging it first. Then with XP you can use gparted but reboot it to make sure it's okay then install Linux. Your better still having the XP bootloader in the mbr if there is a problem.

I just installed XP so I don't think I need to defrag XP. Is that correct?

---

### Post by wilee-nilee on 2010-07-04
> **COKEDUDE said:**
> Whats the Use the largest continuous space option for? Would installing side by side also install a swap partition? 



I just installed XP so I don't think I need to defrag XP. Is that correct?

If you use the autoinstall as you are, the swap is built along with the primary inside a extended partition.

You would have to look at XP to see with the defragger.

If you would like a better defrag program that optimizes as well and is a free download I use this one. It will defrag multiple partitions and HD's at the same time and is faster then the MS one. 
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)

Personally with two disparate OS I treat them separately except for letting grub load the MS.

---

### Post by COKEDUDE on 2010-07-04
Alright I'll test it out. Thx for pointing out that program.

---

