---
title: "Slow file transfer between ext3 hdds"
date: 2010-10-23
forum: General Help
---

### Post by Sylos on 2010-10-23
Hello and thanks for looking.

I recently liberated a 160gig hdd from a BTVision box and popped it into my tower as a Slave drive for extra storage. I know it is running on the same bus as my other drive so transfer speeds between the two will be a little slower but Im getting some seriously slow transfers at times. The first 1gig file I transferred went at around 20mb/sec which is ok but I then tried to copy and paste a folder with 90gig of media in it and the rate dropped to 6-7mb/sec - it took 3 hours!

Both of the drives are ext3 so I cant see why its so slow.

hdparm gives the following
```
/dev/sdb:
 Timing cached reads:   658 MB in  2.00 seconds = 328.26 MB/sec
 Timing buffered disk reads:  180 MB in  3.03 seconds =  59.49 MB/sec


```

I think thats normal (sda seems to test around the same).

Anyone have any idea why its so slow?

Thanks

PS.If it makes any difference Im running 9.10 Karmic

---

### Post by Sylos on 2010-10-24
Bump

---

### Post by katykat on 2010-10-24
It appears Linux has a long standing problem with transfer speed, especially on certain architectures. 

I found Jaunty to be excrucuatingly slow. Meerkat is MUCH faster, but still nowhere near as fast as XP. 

I boot to XP for large file transfers.

---

### Post by coffeecat on 2010-10-24
> **katykat said:**
> It appears Linux has a long standing problem with transfer speed, especially on certain architectures. 

I found Jaunty to be excrucuatingly slow. Meerkat is MUCH faster, but still nowhere near as fast as XP. 

I boot to XP for large file transfers.

@katykat, I suspect you are talking about copying to/from NTFS, which is a Microsoft filesystem. It's hardly surprising that Windows is quicker here. The Linux NTFS-3g driver had to be reverse-engineered and it's inevitable that it will be less efficient.

I suggest you re-read the OP. If you can get Windows XP to copy from one ext3 filesystem to another ext3 fileystem faster than Ubuntu, I will give you £100. :wink:

@Sylos, I have very little to offer. Are either the source or destination filesystems over 90% full? If so, you might be encountering fragmentation issues.

---

### Post by Sylos on 2010-10-24
Cheers for the replies.

From my initial googling I was aware of the NTFS transfer issues. 

katykat - I believe Maverick uses ext4 if I remember correctly which may be one reason for greater speed.

coffeecat - The drive from which the data was copied was pretty full (around 130gig partition with 90gig of files in it) but the target was almost empty. Also, I have tried since with around half the target drive used and the source drive almost empty and still the same sort of speeds.

Must be something clogging up somewhere....

---

### Post by Sylos on 2010-10-28
As a possible solution to my issue im thinking of changing my second HDD to be on the secondary channel but I have a couple of questions as Im a bit green when it comes to this:

1. My current set up is two ribbon cables comming off the MB, each with two connectors. Currently the prmary one has the main OS drive as master and the storage drive as slave. The second cable has just a DVD RW drive on the master - slave is empty. If I put the storage drive onto the second channel does it matter which connector I use (primary or slave). If I attach the drive to the slave will the DVD RW have priority and interrupt it. Similarly, will the DVD RW operation be compromised if I move it to the slave position.

2. If I change the drive over will I need to edit my etc/fstab and alter the moint points in my varying OS's.

Cheers

---

### Post by coffeecat on 2010-10-28
The fact that you must be using PATA drives, not SATA, since you are mentioning master and slave has given me a thought. But first:

> **Sylos said:**
> 1. My current set up is two ribbon cables comming off the MB, each with two connectors. Currently the prmary one has the main OS drive as master and the storage drive as slave. The second cable has just a DVD RW drive on the master - slave is empty. If I put the storage drive onto the second channel does it matter which connector I use (primary or slave). If I attach the drive to the slave will the DVD RW have priority and interrupt it. Similarly, will the DVD RW operation be compromised if I move it to the slave position.

I don't think it would matter whether the secondary drive or DVD drive is in the master or the slave position on the second channel. However, there are two things to consider.

Sometimes when you move secondary drives around on the motherboard, their designation can change - sdb to sdc or sdc to sdb, that sort of thing. It's never happened to me but I've read about it enough to believe it can be a problem. But it may only happen with SATA drives and motherboards where you don't have the master/slave convention. But something to watch out for if something odd happens.

But more importantly - make sure the jumpers are set appropriately on both the HD and DVD if you are going to swap things around. Which brings me to my thought. Your two hard drives - are the jumpers set to master and slave respectively or to cable select on either or both? If you have cable select on any drive, I suggest you change to master or slave as appropriate.

The cable select position on the jumper was a good idea but it can lead to strange things happening - I've experienced some oddities myself - and many people advise avoiding it altogether. I wonder if your bottleneck may be down to using cable select.

---

### Post by Sylos on 2010-10-28
Hello again and hanks for the reply.

I just had a look in the bios and there seems to be no option for detection via cable and the two drives are just optioned as primary and secondary (not master and slave - I expect this is where my ignorance is highlighted and you point out that Primary and secondary refer to something different?)

Im fairly certain that when I bought my first HDD it was SATA ad also Im pretty certain that the storage one is as well. How do I check?

My DVD RW is actually on secondary anyhow so I could just plug it in and have a go - Im not too averse to a bit of fstabbing these days if the need arises.

Will having the two drives on different channels (usually) be fatser? (just checking in case Im wasting my time through my ignorance)

Cheers

---

### Post by coffeecat on 2010-10-28
You seem to be describing the older PATA drives...

[quote="Sylos"]1. My current set up is two ribbon cables comming off the MB, each with two connectors.[/quote]

...yet you believe  you bought a SATA. It's easy to tell the difference. Just look at the connectors and cables:

SATA:

[http://en.wikipedia.org/wiki/Sata](http://en.wikipedia.org/wiki/Sata)

PATA:

[http://en.wikipedia.org/wiki/AT_Attachment](http://en.wikipedia.org/wiki/AT_Attachment)

With the older PATA, you have a wide ribbon cable. One end goes in the motherboard, the other into the master drive, but there's an intermediate connector about three-quarters the way along, nearer the HD end of the cable. The intermediate connector is for the slave drive. 

With SATA you can only have one drive per header on the motherboard. So, if you had two SATA HDs and one SATA DVD drive you would have three of the much narrower SATA ribbon cables.

Once you've looked at the pictures in the links, perhaps you could confirm which type of drives you have but as I'm fairly sure you're talking about PATAs, you don't do anything in the BIOS. The jumpers I referred to are on the HD (or DVD drive), like this:

[http://en.wikipedia.org/wiki/Jumper_%28computing%29](http://en.wikipedia.org/wiki/Jumper_%28computing%29)

Whether a drive is master or slave is determined by which connector it is connected to on the ribbon cable. But it is important to get the jumper position right. 'Cable select' is a convenience because, in theory, you don't have to change it if you change a master to a slave or vice versa. In practice, it is unreliable and might be the cause of your problem. Far better to set the jumper to master or slave as appropriate. If you look on each of the drives you will see a diagram telling you which jumper position is which. There is no standard - each manufacturer uses a different pattern so you need to look on the drive.

---

### Post by Sylos on 2010-10-28
Having looked at the pictures you posted I clearly have PATA drives as you suspected (feeling a little foolish now...).

I will check out the jumpers and post back with the results when I have switched it onto the second channel.

I have done several HDD changes on a few machines and never realised about the jumpers. Guess I have been lucky thus far.

Thank you very much for your help.

---

### Post by Sylos on 2010-10-31
Changed the storage drive onto the secondary channel master and the transfer rate has increased to a sensible level again. I've left the jumpers in the "cable select" position and it seems to be ok when the two are on seperate channels.

Thanks for the help.

---

### Post by coffeecat on 2010-10-31
> **Sylos said:**
> Changed the storage drive onto the secondary  channel master and the transfer rate has increased to a sensible level  again. I've left the jumpers in the "cable select" position and it seems  to be ok when the two are on seperate channels.

I wonder if the cable select jumper position on that drive is happier on  a master position rather than on a slave. Whatever, I'm glad that you are getting decent speeds again.

---

