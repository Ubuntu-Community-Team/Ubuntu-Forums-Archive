---
title: "Need a step by step explanation"
date: 2009-10-13
forum: General Help
---

### Post by texas.chef94 on 2009-10-13
The in quotes paragraph below is a situation I have found myself in frequently. Along with a work around. I need someone with the time and patience to give me a step by step or point me to a article or resource.
Thanks so much


"The main issues you'll run into is every time you want to install a new OS on one of the partitions, it will want to update the MBR so that the computer boots from the newly installed OS. I worked around this by first installing Windows, then installing my primary Linux OS. Next I saved the MBR to disk and thumbdrive (i.e. dd if=/dev/sda of=orig.mbr -bs 512 -count 1) Then, whenever you install the secondary Linux you just rewrite the MBR back to the disk and update the menu.txt in the /boot/grub directory to include the reference to your new partition."

---

### Post by cwbar_1 on 2009-10-13
This _is_ the best how-to on grub I have found.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by texas.chef94 on 2009-10-13
Great explanation.

Thanks

---

### Post by mike555 on 2009-10-13
If you install a bunch of different ones you might do like I do , install grub to the partition your installing to each time and use Gag bootloader to start everything ....  [http://gag.sourceforge.net/](http://gag.sourceforge.net/)    ... I don't think it will boot USB though .......

---

### Post by texas.chef94 on 2009-10-13
Again great information. Now I just have to put this 77 year old brain into overdrive and get all my ducks in place. Planning on repartitioning this 160 GB notebook and want to all the tools at my disposal for the errors I know I will make.

Thank you much

---

### Post by tgalati4 on 2009-10-14
Search "chainloader" in the forums.

Find a local linux club.  The young guys enjoy showing the old timers how its done.  The hands on experience will help you get up to speed.

---

### Post by texas.chef94 on 2009-10-14
> **tgalati4 said:**
> Search "chainloader" in the forums.

Find a local linux club.  The young guys enjoy showing the old timers how its done.  The hands on experience will help you get up to speed.
Thats a thought. Went to one in Dallas 2 years ago. About time for a revisit.

---

