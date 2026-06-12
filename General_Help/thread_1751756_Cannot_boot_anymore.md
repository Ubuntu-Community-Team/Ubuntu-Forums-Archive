---
title: "Cannot boot anymore"
date: 2011-05-07
forum: General Help
---

### Post by StepNjump on 2011-05-07
Hi guys,

I used to work on Ubuntu 10.10 and it was working just fine. However today I wanted to give a try with the version 11.11 so I attempted an upgrade but when I rebooted, it tells me bootmgr is missing on my acer netbook.

If it were a desktop, I wouldn't worry about it. Would just repartition but the problem is that this netbook came with windows 7 and I still use windows 7 for only one piece of software and unfortunately didn't back up win 7 ahead of time.

What must have happened is at a moment during the upgrade, the upgrade tool asked if I want to overwrite grub or something like that. I had a feeling it would happen.

I know all the information is still in the computer. All my partitions are probably just fine but how could I tell grub where my partitions are? Is there a way?

Thank you very much in advance,

Pete.

---

### Post by mr clark25 on 2011-05-07
you just need to reinstall grub, and everything should work like it should. 

you will need to boot from a live cd to fix your system.

go here (i think it still works, but no guarantees...): [http://mrclark.dyndns.org/linux/linux/grubfix.html](http://mrclark.dyndns.org/linux/linux/grubfix.html)

post back if you have issues.

---

### Post by wilee-nilee on 2011-05-07
So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This text file will answer a lot of questions.

---

### Post by StepNjump on 2011-05-09
Thanks for your help guys.. Believe it or not but when I pressed F8, grub somehow fixed itself!

However, I will need to reinstall Ubuntu completely because even though it boots up and I go in linux, everything has been messed up. I guess I should have just said no to overwrite my existing files with the new ones? Oh well.. next time, I will use the graphical interface to upgrade. It will be easier.

Step

---

### Post by StepNjump on 2011-12-20
Thanks for your help guys. I figured it out a while back. thanks.

---

