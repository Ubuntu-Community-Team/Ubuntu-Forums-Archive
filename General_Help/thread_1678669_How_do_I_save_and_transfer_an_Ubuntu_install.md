---
title: "How do I save and transfer an Ubuntu install?"
date: 2011-01-30
forum: General Help
---

### Post by jacatone on 2011-01-30
I'm using Ubuntu 10.04 and my HDD is failing. Is there a way to simply transfer my old install to a new HDD without having to do a fresh reinstall?
Thanks.

---

### Post by nerdy_kid on 2011-01-30
yup -- disk cloning :D  basically, plug the new drive you want to transfer ubuntu on to into your computer, boot up Ubuntu, open up Gparted (install it from the software center if you dont have it) select the partition you have ubuntu installed on, right click it and hit "copy"  then right click the disk you want it installed on and hit "paste".  then hit apply.  After it is done, resize the copied Ubuntu partition to the size that you want it, and add a swap partition, then hit apply.  That should be it, if you dont really know how to do what I said then dont do it because you could wipe out your current Ubuntu and all your files.  I can write out a full howto later, right now I dont have much time.

---

### Post by jacatone on 2011-01-30
So I would connect a second SATA HDD to my MOBO, then run GParted? GParted would see the second drive? Would I need to format the second HDD with ext4 beforehand?

---

### Post by nerdy_kid on 2011-01-30
> **jacatone said:**
> So I would connect a second SATA HDD to my MOBO, then run GParted? GParted would see the second drive? Would I need to format the second HDD with ext4 beforehand?

yes, yes, and no respectively :D

---

### Post by jacatone on 2011-01-30
When I ran GParted, I seem to have both a 5.75GB extended and swap partition. Do I need to save both of them? I've attached a jpeg of GParted.

---

### Post by nerdy_kid on 2011-01-31
ok what you are going to need to do is right click /dev/sda1 and click copy, and then you need to click the /dev/sda button on the top right hand corner and select the hard drive you want to copy too, should be /dev/sdb.  Click right click an unallocated space on the drive and click paste.  The partition should copy over.

[edit]
ignore the swap partition, you can just create a new one on the new drive.

---

### Post by Rhubarb on 2011-01-31
Wow, that's pretty cool nerdy_kid, I didn't know you could use gparted :KS

I had a quick look, and it looks like you can't copy (or for that matter, paste) a mounted partition.

So I think (as I haven't extensively tested this beforehand), you'd be best off loading up a live CD (don't install!), and make sure you get into the desktop (a live desktop), then running gparted from there.
This way both hard drives will be unmounted and hence should work quite nicely :)

There are a few ways to achieve all this, but gparted looks like an easy way to do it.
Otherwise I would've suggested using the clonezilla live CD.
Or getting a list of all the apps installed, install a fresh ubuntu, install the apps, then copy over the user(s) home directory.

I'll put down the gparted copy trick in my mental list of cool things I learnt today :)

---

### Post by nerdy_kid on 2011-01-31
> **Rhubarb said:**
> Wow, that's pretty cool nerdy_kid, I didn't know you could use gparted :KS

I had a quick look, and it looks like you can't copy (or for that matter, paste) a mounted partition.

So I think (as I haven't extensively tested this beforehand), you'd be best off loading up a live CD (don't install!), and make sure you get into the desktop (a live desktop), then running gparted from there.
This way both hard drives will be unmounted and hence should work quite nicely :)

There are a few ways to achieve all this, but gparted looks like an easy way to do it.
Otherwise I would've suggested using the clonezilla live CD.
Or getting a list of all the apps installed, install a fresh ubuntu, install the apps, then copy over the user(s) home directory.

I'll put down the gparted copy trick in my mental list of cool things I learnt today :)

oh yes, thanks for that -- I forgot you cant do that on a mounted partition so yeah grab a LiveCD and do it from there.

btw, this method also works for Windows, which is VERY useful for uping the size of your hard drive.  You also need to copy the MBR though.

---

### Post by mastablasta on 2011-01-31
or use Mint backup tool. you might save the disk space.

---

