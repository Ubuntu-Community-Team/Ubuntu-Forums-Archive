---
title: "How do I clean up my drive...???"
date: 2010-02-15
forum: General Help
---

### Post by robertcoulson on 2010-02-15
Hi, I had [roblems and tried to reinstall Ubuntu 9.10....As you can see Gparted says my drive is a mess....Want to keep NTFS and Linux version 19 and 20, but don't know how to do it.
Please help, Bob

---

### Post by Swagman on 2010-02-15
I'm assuming it's the two swap partitions that's buggin you ?

To disable swap you have to click on it and select switch off... or disable... can't remember which.

THEN remove it and APPLY it.

I appear to NOT have Gparted installed (which is a surprise as I had to do all sorts of trix to get 9:10 installed with multiple sata drives) so I can't immediately check the wordage.

---

### Post by howefield on 2010-02-15
Wouldn't say your disk is a mess, you could however delete one of the swap partitions.

What do you mean by "Linux version 19 and 20" ?

If you have one windows install and one Linux install, I would back up your data, and delete all partitions bar your ntfs one. Then create a / and a /home and a swap.

Then when installing Ubuntu, opt for the manual route when it comes to partitioning and mount the pre created partitions accordingly.

You can view some short videos taking you through this process at sceencasts.ubuntu.com

---

### Post by drs305 on 2010-02-15
sda6 is what is mounted (key icon next to it in the lower panel) and being used by Ubuntu, so you probably want to delete sda8. As mentioned, sda6 will need to be turned off. Select the sda6 swap partition, then Partition, Swapoff. You will now be able to delete the other swap partition by selecting it and then Partition, Delete.\

If there is more you want to do and don't know how, please elaborate.

---

### Post by Swagman on 2010-02-15
[img]http://www.upload3r.com/serve/150210/1266248316.jpeg[/img]

---

### Post by robertcoulson on 2010-02-15
What I meant (And I do sound stupid...sorry) is generic version 20 is what I am running now...So I originally had my 80 gig hard drive split, 40 (approx) gig on XP and 40 gig on Ubuntu 9.10
Bob

---

### Post by robertcoulson on 2010-02-15
OK, I looked at Gparted...NOW, I guess I want to take all the disk space from SDA7 and put it back to SDA5....Correct...??...And delete SDA8....???
Bob

---

### Post by drs305 on 2010-02-15
If you want to delete sda7 and expand your system partition you will have to do it from the LiveCD or other "rescue" type cd. This is because the / partition must not be mounted while you perform actions on it.

I wrote a guide on expanding the / partition. About half way down it offers some techniques and procedures you might find helpful.

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by robertcoulson on 2010-02-15
Thank you very much
Bob

---

### Post by robertcoulson on 2010-02-15
Sorry...could not find your documentation.....(stupid eh)...Guess I will have to live with a smaller Ubuntu partition.
Thanks, Bob

---

### Post by SemiBuz on 2010-02-15
As I still don't clearly see what are you after, check [this guide]("http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk") - I'm pretty sure it covers enough to be able to get things done.

---

### Post by robertcoulson on 2010-02-15
Hi semibuz...When I look at gparted, I have 2 linux partitions SDA5 and SAD7...Wanted to remove SDA7 and put more space on SDA%....But I am having a problem getting my mind around it...See attachment.
Bob

---

### Post by SemiBuz on 2010-02-15
sda5 holds the root so you can't resize / delete it while it's mounted - you'll need a LiveCD.
Once you've access to it while it's NOT mounted, delete sda7 and modify the sda5 ( just pull up the size to 100% ) - hit apply and you're done.

** Why do you need 2 swap's ?

---

### Post by robertcoulson on 2010-02-15
Thanks semibuz...That is more clear, I should use gparted on the live cd and then do my thing, is that correct...???
Bob

---

### Post by SemiBuz on 2010-02-15
Yes. Let us know the outcome.

---

### Post by robertcoulson on 2010-02-15
Thank you very, very much...I will.
Bob

---

### Post by robertcoulson on 2010-02-15
It was a diaster...After I put in the Live CD and made my Ubuntu partition bigger and applied the change, it looked great...When I rebooted, I got an ugly "Unknown filesystem" error...Kept me at a "Grub rescue" input..Had to reinstall Ubuntu, now I am back to where I began, but even though my Ubuntu partition is still small, it works and I am afraid to try anything else just in case I can't access XP or Ubuntu forever...Thanks for trying guys, I better leave well enough alone.
Robert

---

### Post by robertcoulson on 2010-02-15
One last thing...see attachment, can I delete swap SDA7 and SAD( without scrwing up my system...???

---

### Post by robertcoulson on 2010-02-15
Sorry SDA7 and SDA9 (Bad writer)
Robert

---

### Post by drs305 on 2010-02-16
> **robertcoulson said:**
> Sorry SDA7 and SDA9 (Bad writer)
Robert

Yes. Turn off swap by highlighting sda6, then Partition, Swapoff. You can then delete sda7 and sda9. You can then expand sda8 to the right to incorporate the new unallocated space into sda8 if you wish.

---

### Post by Swagman on 2010-02-16
Personally, if that'd been me (I've done exactly what you are trying to do) I'd have booted from the live cd and removed all linux partitions, including all the swapfiles, rebooted into the live cd again and re-installed fresh.

Which seems like the best course of action as you have re-installed anyway.

---

### Post by robertcoulson on 2010-02-16
Ya swagman...Me not being a Ubuntu guru, that was my only alternative..DRS305 really went out of his way to try and get me to where I wanted to be, but, got all screwed up, and re-install was my only (last) resort...
Robert

---

