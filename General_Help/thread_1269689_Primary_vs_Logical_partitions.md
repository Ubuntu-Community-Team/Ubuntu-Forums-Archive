---
title: "Primary vs Logical partitions"
date: 2009-09-18
forum: General Help
---

### Post by portalhometech on 2009-09-18
In plain English can someone tell me the difference between primary and logical partitions.

I understand that you can have 4 extended partitions on a drive. Logical can exist in extended while primary are outside?

Lets say i have two hard disks in a PC and i was going to mount /home to the second HDD and have the swap and "/" on the first HDD. would it make sense to set the first drive up as swap and Primary for the full size of the drive?

What is the best setup for a laptop where i have only one drive? 

Most of my windows installs have used one partition for C:\ for a long time since hard drives are so large and cheap now. im still learning the linux way.

---

### Post by Liolikas on 2009-09-18
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

---

### Post by DasEi on 2009-09-18
the standard for a hdd is that you can have up to (maximum) 4 primary partitions.
Each of them can contain an extended partion.
inside the extended space you can have numerous (don't know exact limit, never reached it) logical drives, which can be used like primarys.

If you ever want to crypt your system, make sure to have a seperate /boot.

The next part : yes it is possible to put /home on a second disk.

              : depends what you will do with that lappi, automated install
                suits most common needs

---

### Post by Liolikas on 2009-09-18
In most simple talk hdd can have 4 primary partition but for some it was not enough so they designed extender partition which can be divided into even more partitions. Everything else is just technical stuff.

---

### Post by portalhometech on 2009-09-18
Thanks guys for the fast responses. I understand what you are saying. What i can understand (forgive me for years and years of windows habits) is why not have one primary for swap and one primary for everything else? Maybe one primary for swap, one for everything but /home and put /home on its own pri? Do you only need to use ext/logical partitions if space is an issue or if you plan on changing your system without having to wipe the whole drive?

---

### Post by DasEi on 2009-09-18
well, it's a question of flexibility, once you used your 4 primarys up, can't go anyfurther, if you ( as the ubu-installer does by default) create just one extended, can resize and shove / add /delete the logic ones in side as your needs change, always nice to have a primary in sparse to -come whatever may

assuming hardrive is big enough, think of booting 6 OS'es or more ...

---

### Post by dandnsmith on 2009-09-18
> **DasEi said:**
> the standard for a hdd is that you can have up to (maximum) 4 primary partitions.
Each of them can contain an extended partion.
inside the extended space you can have numerous (don't know exact limit, never reached it) logical drives, which can be used like primarys.


I'm afraid that that isn't correct.

Using the MSWIN partition table, which is what we're discussing here (there are others), you can have up to 4 primaries.
If you need more partitions, then one (or possibly more) of your primaries has to be an extended partition - which acts as a sort of container for your logical partitions.

Why not always use logicals inside a primary container? Its because (mainly) of the historic booting requirements.

---

### Post by portalhometech on 2009-09-18
So if space and future expansion plans permit you dont need ext/logical partitions primary will work fine? However if i require flexibility then extended partion(s) need to be created to hold as many logical partitions as i need. I think i read somewhere that the limit is a number in the 60's...true?

---

### Post by DasEi on 2009-09-18
I never reached that border, from a quick look up it should be 63 on ide/sata drives, 15 for scsi.
Apart from that, did I describe something else then dandnsmith did?
Wasn't my intent.

---

### Post by portalhometech on 2009-09-18
I think y'all answered my questions. i guess in my head it just feels weird. On Windows machines i have made the C:\ the full size of the HDD for so long anyways. If the hard drive blew chow you have bigger problems than how your partitions are setup. Unless you had partitions setup on different hard drives. So, case closed.

I do appreciate the folks in the Ubuntu forums. All of my newb questions have been answered with no attitude from the more advanced users. I can tell i made the right choice with Ubuntu. Great community support. Thanks again.

---

### Post by dandnsmith on 2009-09-19
> **DasEi said:**
> I never reached that border, from a quick look up it should be 63 on ide/sata drives, 15 for scsi.
Apart from that, did I describe something else then dandnsmith did?
Wasn't my intent.

I appreciated your intent, but was concerned that it could be misread/misinterpreted - I've seen evidence of confusion over these details.

I'm not sure about SCSI limitations - the MSWIN wasn't developed in that context, but arose as a result of a totally different set of OS's with a different view of things (on rather more expensive hardware)

---

