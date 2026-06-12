---
title: "Can a windows partion effect Ubuntu's abilities?"
date: 2009-08-13
forum: General Help
---

### Post by cptrohn on 2009-08-13
In regards to multi-media etc?

I have a laptop that I recently set-up to dual boot since I am going to be going to school for IT and talking with the instructor he said it would be needed in class to have both a windows partition and a linux partition.. So I reconfigured my laptop to dual-boot windows Vista (it's what was pre-loaded so I used my rescue discs) and Ubuntu 9.04.  After I set up Vista I then split the HDD in half (500gb HDD) on the Ubuntu install.. I of course edited the software sources, enabled medibuntu and installed ubuntu restricted extras and libdvdcss2..... then a funny thing happened, I could not get any CD's or DVD's to mount in ubuntu.....  frustrated I wiped the HDD and then just re-installed Ubuntu 9.04 as the sole OS again and the exact same CD's and DVD's mounted and played with no problem.. I have not put Vista back on the machine as yet.. But doesn't it seem odd with a Windows partition I couldn't do this but without a Windows partition things work as they should?

---

### Post by mike555 on 2009-08-13
Windows on a separate partition should not effect Ubuntu , the only way it could is if you installed the Windows program that lets it write to Ext partitions , even then it should not effect cd play.....

---

### Post by pmlxuser on 2009-08-13
strange thing indeed i don't understand it myself but cout it be that the DVD/cd were just not automounting. did you try to mount them manually? but still i would after this installation install windows again and then reinstall grub.

the point is as long as there is enough space on ubuntu partition and enough RAM you should not have problems.

---

### Post by cptrohn on 2009-08-13
OK, thats what I was thinking is that it shouldn't effect it..

What is the name of the windows program that allows it to write to Ext3?  Maybe if I just uninstall that program it won't happen then?

---

### Post by tgeer43 on 2009-08-13
> **cptrohn said:**
> OK, thats what I was thinking is that it shouldn't effect it..

What is the name of the windows program that allows it to write to Ext3?  Maybe if I just uninstall that program it won't happen then?There's more than one but this one is freeware and works quite well. Easy to install and uninstall too. Have a look here:

[http://fs-driver.org/index.html](http://fs-driver.org/index.html)

Have fun!

tgeer

---

