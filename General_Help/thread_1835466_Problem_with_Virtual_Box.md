---
title: "Problem with Virtual Box"
date: 2011-08-29
forum: General Help
---

### Post by lu89 on 2011-08-29
Hi Guys, 
I hope I'm right here. I have a problem with Virtual Box 4.2. If I want to install Win Xp in it, it gaves me an error massege, that the HDD Capacity is too low. It doesn't matter how big I make the Virtual Disk. 
I hope you can help me.

---

### Post by seawolf167 on 2011-08-29
Do you have enough room on your physical hard drive? Please post the output of

```
df -h
```

How big have you tried to make the virtual hard drive partition?

---

### Post by Horadranin on 2011-08-29
Try to delete and recreate the virtual machine and the virtual disk again. Make sure you selected the right operation system while creating the VM and the virtual HD size is at last 5G or 8G. Also, make sure your host computer have enough space for the virtual machine.

I never faced a problem installing XP in Virtualbox, but i never tried install it in the 4.2 so I don't know if it may be a version bug.

---

### Post by lu89 on 2011-08-29
My Ubuntu Partition is 195Gb big (about 12Gb full). My Virtual HDD was 35 Gb (enough for Xp).

---

### Post by haqking on 2011-08-29
> **lu89 said:**
> Hi Guys, 
I hope I'm right here. I have a problem with Virtual Box 4.2. If I want to install Win Xp in it, it gaves me an error massege, that the HDD Capacity is too low. It doesn't matter how big I make the Virtual Disk. 
I hope you can help me.

there isnt a version 4.2, or do you mean version 4.1.2

anyways yeah as above, make sure you have enough space free in the location where your VM HDD will be stored and make sure it is at least 8Gb for the VM

---

### Post by seawolf167 on 2011-08-29
> **lu89 said:**
> My Ubuntu Partition is 195Gb big (about 12Gb full). My Virtual HDD was 35 Gb (enough for Xp).

If you delete this virtual drive and re-create it to you run into the same issue?

---

### Post by Horadranin on 2011-08-29
> **lu89 said:**
> My Ubuntu Partition is 195Gb big (about 12Gb full). My Virtual HDD was 35 Gb (enough for Xp).
And recreating the VM from scrath didn't helped?

Is the Windows installer or the Virtualbox the one giving the message?

---

### Post by haqking on 2011-08-29
> **Horadranin said:**
> And recreating the VM from scrath didn't helped?

Is the Windows installer or the Virtualbox the one giving the message?

we dont know, you are the one reading it ;-)

when you see the message post a screen dump here so we can see

---

### Post by Horadranin on 2011-08-29
> **haqking said:**
> we dont know, you are the one reading it ;-)

when you see the message post a screen dump here so we can see
Ops, I think you made a little mess.
I'm not the OP. I'm just trying to help too :)

---

### Post by haqking on 2011-08-29
> **Horadranin said:**
> Ops, I think you made a little mess.
I'm not the OP. I'm just trying to help too :)

OH yeah....LOL

misread it, sorry ;-)

---

### Post by lu89 on 2011-08-29
> **haqking said:**
> there isnt a version 4.2, or do you mean version 4.1.2


I meant 4.1.2

---

### Post by seawolf167 on 2011-08-29
Did deleting and re-creating the virtual drive help?

---

### Post by lu89 on 2011-08-29
> **seawolf167 said:**
> Did deleting and re-creating the virtual drive help?

It doesn't help. But will try it again tomorrow.

---

