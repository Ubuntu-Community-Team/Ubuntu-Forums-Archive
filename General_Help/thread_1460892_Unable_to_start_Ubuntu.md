---
title: "Unable to start Ubuntu"
date: 2010-04-23
forum: General Help
---

### Post by scottym on 2010-04-23
When booting up my IBM Thinkpad Ubuntu stalls giving the following messages:

Cannot open root device "uuid=58a5831c-5757-49f8.....

Kernal Panic - not syncing: Unable to mount root fs on unknown-block

Spurious ACK on isa0060/serio0. Some program might be trying to access hardware directly.

I am or was using Hardy. 

It seems to me that the program is telling me it can't find the hard drive or the partition where the OS resides. I have my drive partitioned with into sections for booting, the OS and my Home directory. 

Any ideas on what I can do here. Please don't suggest a fresh install as my cd drive is broken so that is not an option. 


Thanks

---

### Post by ajgreeny on 2010-04-23
If this happened after installing a new kernel update, just try booting to an earlier kernel instead of the latest new one.  If you don't see a grub menu when you boot, hit Esc soon after switch on, or when you see the "Starting grub" prompt on screen.

---

### Post by scottym on 2010-04-27
my grub menu has three options: normal start up, recovery mode and memmory test. The recovery mode gives the same error messages when booting. Any other ideas I can try? Thanks.

---

### Post by P4man on 2010-04-27
If its not a fresh kernel (and it seems unlikely they would introduce such a caliber of bug at this stage of ubuntu 8.04) then I fear your hdd just gave the ghost.

Can you make a [bootable USB stick]("http://unetbootin.sourceforge.net/") with an ubuntu image and boot that?

---

### Post by scottym on 2010-04-28
I'll give that a try and let you  know. Thanks

---

### Post by scottym on 2010-09-22
The link for a bootable flash drive is taking me to a storage tier facility. Any ideas on where to get a falsh loaded so it will boot a laptop?

---

### Post by BobVila on 2010-09-22
> **P4man said:**
> If its not a fresh kernel (and it seems unlikely they would introduce such a caliber of bug at this stage of ubuntu 8.04) then I fear your hdd just gave the ghost.

Can you make a [bootable USB stick]("http://unetbootin.sourceforge.net/") with an ubuntu image and boot that?

If you do get a bootable USB drive going, see if you can mount your filesystem. You could also run some smart tools to see if the drive has bought the farm.

---

### Post by scottym on 2010-09-24
I've tried doing a baoootable usb without success Possible I am doung it wrong. the message I am getting say it cannot access the HD so that could be the proble. Somthinh similar happened before and I changed the HD numbers in some file and was working again. At this stage when the grub menu loads I can c to enter the options to give tsome basic command but I a at alos as towhat to tell it todo.

---

