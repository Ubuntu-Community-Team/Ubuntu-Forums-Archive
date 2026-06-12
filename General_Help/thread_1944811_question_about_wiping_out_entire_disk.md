---
title: "question about wiping out entire disk"
date: 2012-03-21
forum: General Help
---

### Post by kdane4 on 2012-03-21
I'm dual booting win 7 and ubuntu on a single hard disk and accidentally converted my basic disk to a dynamic one. I'm planning to wipe out the disk entirely(maybe using software like DBAN, etc) 

My question would be, after wiping out the disk, is it gonna be automatically converted to basic disk after I install windows? I prefer  installing windows first before ubuntu.

I already backed up my files  so reinstallation is cool with me. 

Thanks!

---

### Post by dcstar on 2012-03-22
> **kdane4 said:**
> I'm dual booting win 7 and ubuntu on a single hard disk and accidentally converted my basic disk to a dynamic one. I'm planning to wipe out the disk entirely(maybe using software like DBAN, etc) 

My question would be, after wiping out the disk, is it gonna be automatically converted to basic disk after I install windows? I prefer  installing windows first before ubuntu.


[LIST=1]
[*]"Wiping" is totally pointless.
[*]Ubuntu can only read "Basic" Windows partitions.
[*]Why not just convert the Windows partition back to Basic?
[/LIST]

---

### Post by whiskers751 on 2012-03-22
I would NOT recommend wiping your HDD. I did it and it stopped Ubuntu running!

---

### Post by kdane4 on 2012-03-22
> **dcstar said:**
> [LIST=1]
[*]"Wiping" is totally pointless.
[*]Ubuntu can only read "Basic" Windows partitions.
[*]Why not just convert the Windows partition back to Basic?
[/LIST]

1. Im already backed up so its ok with me.
2. That is correct, thats why I wanted to convert it back to basic
3. If you can teach me how to do it that would be lovely. Like I said I only have 1 hard drive and my operating systems is installed on that disk. I've seen some tutorials on how to change back to dynamic, but none of them seemed to cover how to do it if your OS is installed on the dynamic disk. 

Thanks for the reply

---

### Post by kdane4 on 2012-03-22
> **whiskers751 said:**
> I would NOT recommend wiping your HDD. I did it and it stopped Ubuntu running!

Im ok with reinstallation coz I already backed up all my important files. :)

thanks for the reply

---

### Post by whiskers751 on 2012-05-02
No - there might be some hidden important files that reside on the HDD that make Ubuntu work....
Don't wipe a hard drive - just change OSes. :)

---

### Post by Mark Phelps on 2012-05-03
> **whiskers751 said:**
> Don't wipe a hard drive - just change OSes. :)

Did you even bother to READ what the OP said?? 

His partitions got converted to Dynamic Disks -- which the Ubuntu installer is unable to recognize.  So he can't "change OSes" without losing data unless he's able to covert them back to Basic Volumes.

---

### Post by dcstar on 2012-05-03
> **kdane4 said:**
> 1. Im already backed up so its ok with me.
2. That is correct, thats why I wanted to convert it back to basic
3. If you can teach me how to do it that would be lovely. Like I said I only have 1 hard drive and my operating systems is installed on that disk. I've seen some tutorials on how to change back to dynamic, but none of them seemed to cover how to do it if your OS is installed on the dynamic disk. 

Thanks for the reply

Ok, old thread but:

Boot your Windows install CD and do a "Repair" which will reinstall the Windows boot loader. Boot up Windows and use the Disk Manager to convert the disk back to basic.

Then search out the various instructions of restoring Grub and then everything should work again.

---

### Post by kdane4 on 2012-05-03
thanks guys! Forgot to report back. I borrowed a copy of easeus partition tool from a friend (its a paid version.. The free version doesnt have a feature of using a live environment so it wont work in my case.) Booted it from a live cd and successfully converted it back to basic. I will now mark this as solved.

---

