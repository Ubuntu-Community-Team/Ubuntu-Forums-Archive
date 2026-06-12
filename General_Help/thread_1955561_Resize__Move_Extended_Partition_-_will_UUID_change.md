---
title: "Resize / Move Extended Partition - will UUID change?"
date: 2012-04-09
forum: General Help
---

### Post by cryptotheslow on 2012-04-09
Hi,

I've attached a screenie from gParted of how things are now. Ubuntu is installed in sda5 with encrypted swap (not mounted) in sda6. sda1 - 3 are what came configured with the Win7 install on the laptop.

My plan is to shrink "DATA" sda3 a lot using Win tools, then boot to a liveCD/USB, shift sda4 left into the free space, expand it to fill the free space and then create a new ext4 logical partition.

So yeh - will the UUIDs of the existing partitions change? And is there anything I need to be concerned with regards GRUB2?

I think it will all be fine - just asking in case I forgot something obvious (not unprecedented for me :D )

Thanks

---

### Post by ratcheer on 2012-04-09
Yes, I am pretty sure it will change.

Tim

---

### Post by Bucky Ball on 2012-04-09
Make sure you run:

```
sudo update-grub
```

... once back at the desktop.

---

### Post by dylan07 on 2012-04-09
I would backup incase it breaks the system!

---

### Post by cryptotheslow on 2012-04-09
Thanks all so far.

>ratcheer - I thought UUIDs only changed when you reformatted a partition. In this case I'm just moving them. Is my understanding wrong? :(

>Bucky Ball - if something changes enough to require an update-grub then it's unlikely I'll be able to boot the Ubuntu installed desktop to be able to run it. :(

>dylan07 - thanks for the reminder. Everything is backed up. :)

Going on this I think I shall keep my chroot tutorials close to hand just in case. Thankfully I have a couple of other PCs running should I hose this one in the process, I'd certainly be a lot more cautious if this were my only machine.

Thanks again :)

---

### Post by drs305 on 2012-04-09
I don't think resizing will change the UUID but moving it might. In fact, when I move a partition using the latest versions of Gparted a warning is displayed indicating it could break the system.

It would be best to record the UUIDs before and after your disk operations. If they change, one thing that hasn't been mentioned is that you can reset them to the original UUID using *tune2fs*. 

Compare everything before rebooting - especially update Grub 2 and take a look to ensure your /etc/fstab file is still correct. Most problems are much easier to solve prior to rebooting!  ;-)

---

### Post by cryptotheslow on 2012-04-09
Thanks drs305, that's certainly a better perspective than reboot and hope for the best then fix it if it is broke. :)

Question in my mind - how does GRUB2 reference partitions - by UUID or by placement on the disk or something else?

My /etc/fstab references UUIDs, but for /etc/fstab to be read the / filesystem must already be mounted no? Yet / is defined in /etc/fstab - catch 22.

My assumption then (welcome to be shot down) is that GRUB2 must have stored knowledge of my partition layout.

Hmm... I really ought to move on from having to understanding how every little thing works, it's not healthy. :lolflag:

---

### Post by drs305 on 2012-04-10
> **cryptotheslow said:**
> Thanks drs305, that's certainly a better perspective than reboot and hope for the best then fix it if it is broke. :)

Question in my mind - how does GRUB2 reference partitions - by UUID or by placement on the disk or something else?

Grub 2 uses UUIDs to identify partitions. It also has a limited search capability to find it's boot files.

The UUID feautre can be disabled in the /etc/default/grub file but using UUIDs is more reliable than relying on device names such as sda1, sdb1, etc.

---

### Post by cryptotheslow on 2012-04-10
Thanks drs305. I've had problems in the past caused by device names changing around as drives are added and removed - the UUID approach certainly seems more robust.

Anyway - change of plan here. I want to do a reinstall once 12.04 is released (currently on the alpha/beta) as I have installed about 10 different desktop environments to experiment with and am getting all kinds of weirdness now each time one of them pulls down a bunch of updates. It's going to be quicker to nuke it and reinstall rather than try and clean it up - so I'll mess with the partitions between nuking it and reinstalling. Think I'll just do away with the DATA partition, expand the extended partition then install a fresh 12.04 into a new logical partition in there keeping the existing install's partition intact so I can refer back to it for various config stuff.

Thanks again everyone - much appreciated. :)

---

