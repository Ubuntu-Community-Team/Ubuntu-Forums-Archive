---
title: "Convert hardware RAID to software RAID? Possible?"
date: 2010-01-17
forum: General Help
---

### Post by HighCommander540 on 2010-01-17
So I know I am going to get people entering this thread to complain how stupid it is to convert to a software from a hardware RAID. Hear me out first.

I have a 1TB external WD hard drive. And the problem is the hardware RAID controller has failed. I am pretty sure its just the controller and not the hard drives, because I have put them in another computer and they check out. I just don't know how to use RAID.

So the issue is I am wondering if it is possible to take to hard drive that were in a RAID array and still have data on them and put them in a software array. Cause I need to get the data off of the hard drives. Is it possible to do this and keep the data or is there something special about each array that is made that makes it so I can't?

It was two 500GB hard drives in RAID 0. So I need to know how to put them back together to work as one if possible and how to do it...

I appreciate any help. I have a lot of data I really need on there.

---

### Post by LoneWolfJack on 2010-01-17
it's very unlikely that you can, yet almost nothing is impossible in the linux world.

you would have to look for a program that can deal with your hardware raid controllers way of storing the data (all vendors have their own way of writing RAID data, often they also use different methods for different products). even then, the program would have to first copy all data out of that array to make it readable by the raid software.

as you should have a backup anyway - especially with a raid 0 - just set up a new RAID.

---

### Post by HighCommander540 on 2010-01-17
> **LoneWolfJack said:**
> it's very unlikely that you can, yet almost nothing is impossible in the linux world.

you would have to look for a program that can deal with your hardware raid controllers way of storing the data (all vendors have their own way of writing RAID data, often they also use different methods for different products). even then, the program would have to first copy all data out of that array to make it readable by the raid software.

as you should have a backup anyway - especially with a raid 0 - just set up a new RAID.

You don't understand the external was the backup for all of my data. I don't have another copy of it. Its not a actual RAID that I set up. It an external hard drive case from western digital that they have two drives in a RAID 0 array. Just the two of them with a tiny *** controller. There is no way to back up or do anything the controller fried...So now its just two drives with half the unreadable data on each.

---

### Post by sports.car.guy on 2010-01-17
> **HighCommander540 said:**
> You don't understand the external was the backup for all of my data. I don't have another copy of it. Its not a actual RAID that I set up. It an external hard drive case from western digital that they have two drives in a RAID 0 array. Just the two of them with a tiny *** controller. There is no way to back up or do anything the controller fried...So now its just two drives with half the unreadable data on each.


It will not be a possibility as far as I know to do what you want. I got a drive off of a friend that was 1Tb with 4 EIDE drives in it. The internal controller died so I installed them using an EIDE card into one of my systems. The hardware raid decides where data is written and odds are software raid won't like it. I tried to do a recovery like you are talking about for my friend to no avail.

---

### Post by markp1989 on 2010-01-17
> **HighCommander540 said:**
> So I know I am going to get people entering this thread to complain how stupid it is to convert to a software from a hardware RAID. Hear me out first.

I have a 1TB external WD hard drive. And the problem is the hardware RAID controller has failed. I am pretty sure its just the controller and not the hard drives, because I have put them in another computer and they check out. I just don't know how to use RAID.

So the issue is I am wondering if it is possible to take to hard drive that were in a RAID array and still have data on them and put them in a software array. Cause I need to get the data off of the hard drives. Is it possible to do this and keep the data or is there something special about each array that is made that makes it so I can't?

It was two 500GB hard drives in RAID 0. So I need to know how to put them back together to work as one if possible and how to do it...

I appreciate any help. I have a lot of data I really need on there.

i would recommend you try ebay to see if you can get a controller for the external drive?

---

### Post by HighCommander540 on 2010-01-17
Thanks for the info. I think what I am going to do is send it in to WD and tell them to just give me a new case and keep the hard drives and data.

As a precaution though I was wondering...If I make a full partition backup of each of the hard drives and I get the new external back and they didn't keep my data. Would I then be able to put the respective partitions back on and it work? Assuming of course that is the same hardware is still used.

---

### Post by lukeiamyourfather on 2010-01-17
> **HighCommander540 said:**
> So I know I am going to get people entering this thread to complain how stupid it is to convert to a software from a hardware RAID. Hear me out first.

I have a 1TB external WD hard drive. And the problem is the hardware RAID controller has failed. I am pretty sure its just the controller and not the hard drives, because I have put them in another computer and they check out. I just don't know how to use RAID.

So the issue is I am wondering if it is possible to take to hard drive that were in a RAID array and still have data on them and put them in a software array. Cause I need to get the data off of the hard drives. Is it possible to do this and keep the data or is there something special about each array that is made that makes it so I can't?

It was two 500GB hard drives in RAID 0. So I need to know how to put them back together to work as one if possible and how to do it...

I appreciate any help. I have a lot of data I really need on there.

Short answer is no, you can't take an array from a hardware RAID controller and read it with software RAID in Linux. I'm sure its ***possible***, but probably not in the sense of the word that you mean (e.g. without hiring a team of developers or spending months/years of your own time). Buying another of the exact same product might allow you to hook those drives into it and read the data. That's pretty much what a hard drive recovery service would do. In case its not obvious now, keep a backup of anything you don't want to lose to avoid situations like this. Cheers!

---

### Post by lukeiamyourfather on 2010-01-17
> **HighCommander540 said:**
> Thanks for the info. I think what I am going to do is send it in to WD and tell them to just give me a new case and keep the hard drives and data.

As a precaution though I was wondering...If I make a full partition backup of each of the hard drives and I get the new external back and they didn't keep my data. Would I then be able to put the respective partitions back on and it work? Assuming of course that is the same hardware is still used.

They won't do that, they'll want to whole thing back and they won't save the data or disks for you (because that's what hard drive recovery services are for). Making a clone of the disk will probably do you no good unless its with a bit for bit tool like "dd", and even then its still hit and miss since its from a RAID array.

---

### Post by HighCommander540 on 2010-01-17
> **lukeiamyourfather said:**
> Short answer is no, you can't take an array from a hardware RAID controller and read it with software RAID in Linux. I'm sure its ***possible***, but probably not in the sense of the word that you mean (e.g. without hiring a team of developers or spending months/years of your own time). Buying another of the exact same product might allow you to hook those drives into it and read the data. That's pretty much what a hard drive recovery service would do. In case its not obvious now, keep a backup of anything you don't want to lose to avoid situations like this. Cheers!

The hard drive was my backup...

Thanks, I guess I am just screwed. Unless I want to fork over a ridiculous amount of money to get the data recovered.

---

### Post by lukeiamyourfather on 2010-01-17
> **HighCommander540 said:**
> The hard drive was my backup...

Thanks, I guess I am just screwed. Unless I want to fork over a ridiculous amount of money to get the data recovered.

If that was the backup then where's the original? Sounds like that was the only copy of the data (e.g. not a backup). :-s

---

### Post by HighCommander540 on 2010-01-17
> **lukeiamyourfather said:**
> If that was the backup then where's the original? Sounds like that was the only copy of the data (e.g. not a backup). :-s

I backup up all of the info to the hard drive so I could do a reformat of my desktop hard drive. Then I did the reformat and the hard drive stopped working sometime during the installation.

So I lost the backup as I was installing, bad luck.

---

### Post by lukeiamyourfather on 2010-01-17
> **HighCommander540 said:**
> I backup up all of the info to the hard drive so I could do a reformat of my desktop hard drive. Then I did the reformat and the hard drive stopped working sometime during the installation.

So I lost the backup as I was installing, bad luck.

Have you tried it on another computer? Its possible when you reinstalled it broke maybe a driver, or there's a bug. Its worth trying if you haven't already.

---

### Post by Cheesemill on 2010-01-17
When my hardware RAID controller (4x 250GB RAID5) died on me I was able to get my data back by plugging the drives into my motherboard IDE channels and using [RAID Reconstructor ]("http://www.runtime.org/raid.htm")to reconstruct the data.

2 drawbacks - It's Windows only and will cost you $99.

There is a free trial you can use to see whether or not it will work before shelling out the cash.

---

### Post by HighCommander540 on 2010-01-17
> **lukeiamyourfather said:**
> Have you tried it on another computer? Its possible when you reinstalled it broke maybe a driver, or there's a bug. Its worth trying if you haven't already.

No, its not possible. I know the controller died. Because it was a NAS/SAMBA external hard drive and I can't connect to it with any computer that could before. There were no drivers at all installed for it. It worked on multiple systems. And now it doesn't.

> **Cheesemill said:**
> When my hardware RAID controller (4x 250GB RAID5) died on me I was able to get my data back by plugging the drives into my motherboard IDE channels and using [RAID Reconstructor ]("http://www.runtime.org/raid.htm")to reconstruct the data.

2 drawbacks - It's Windows only and will cost you $99.

There is a free trial you can use to see whether or not it will work before shelling out the cash.

Hey, thanks. Does it only recover windows RAID? Or can it recover anything? Because I have Windows but the RAID was with Linux.

Also, problem I tried to do this...I don't have enough SATA power cords to run my hard drive and both of the other drives to have it check the RAID array. I have enough transfer cables just not the power cables. So I can't even try.

---

### Post by Cheesemill on 2010-01-17
> **HighCommander540 said:**
> Hey, thanks. Does it only recover windows RAID? Or can it recover anything? Because I have Windows but the RAID was with Linux.
Not sure if it can handle ext, my drives were NTFS.

> Also, problem I tried to do this...I don't have enough SATA power cords to run my hard drive and both of the other drives to have it check the RAID array. I have enough transfer cables just not the power cables. So I can't even try.
Could you unplug your CD drive?

---

### Post by Cheesemill on 2010-01-17
Just found this post:
[http://pario.no/2009/01/19/mount-a-disk-image/](http://pario.no/2009/01/19/mount-a-disk-image/)

You'll need a spare 1TB drive to store the disc image that RAID Reconstructor creates.

---

### Post by HighCommander540 on 2010-01-17
> **Cheesemill said:**
> Not sure if it can handle ext, my drives were NTFS.


Could you unplug your CD drive?


Um, CD drives and SATA power cords are not the same...

> **Cheesemill said:**
> Just found this post:
[http://pario.no/2009/01/19/mount-a-disk-image/](http://pario.no/2009/01/19/mount-a-disk-image/)

You'll need a spare 1TB drive to store the disc image that RAID Reconstructor creates.

Well **** that is gay. I would need more than a 1TB actually. Because a full partition wouldn't fit on a 1TB drive.

---

### Post by Cheesemill on 2010-01-17
> **HighCommander540 said:**
> Um, CD drives and SATA power cords are not the same...

They are if you have a SATA CD drive.

---

