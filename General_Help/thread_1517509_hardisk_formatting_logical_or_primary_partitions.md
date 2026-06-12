---
title: "hardisk formatting logical or primary partitions?"
date: 2010-06-25
forum: General Help
---

### Post by complience on 2010-06-25
I'm doing a new installation of ubuntu 32bit 10.04

I have a 160 sata HD.

My planned partitions are such

2gig Swapspace
2gig Swapspace

40gig /
116gig /home/

My question is should these be logical or primary partitions?

---

### Post by justleen on 2010-06-25
you can only have four primary partitions. If you need more, you can create a logical partitions, which in turn can hold 4 partitions (including more logical ones, which each can contains 4 partitions, etc etc)
Consisdering you only have 4 partitions, you could use four primary ones.

(Why would you want two swap partitions? )

---

### Post by kalistona on 2010-06-25
you have 2 swap space ? well...
a primary is all the space alloued.
in this space you decide to take a part for home/cryped/swap p.e.
i am a little surprised that your 'home' be 120GO and your system 40 but it is your choise.
anyway from gparted; you can, with your mouse, change how many GO for each part. 
good fun.

---

### Post by complience on 2010-06-25
With two swaps, this means if you have two applications that require to use the swapspace they can both run concurrently. 

an Ubuntu system doesnt need any more than 40gig, why would I want to use up space that I could be using for my /home/ files?

---

### Post by Ordes on 2010-06-25
why 2 swap? 

also i think 40 gb for / is quite a lot..

i would make
20gb /

4gb swap
Rest gb /home

2 primary:
1) for /
2) for /home & swap  (divide primary into 2 logical)

or you can make 3 primary if you prefer

>> a system should always be installed into primary. whereas logical can be used for data etc....

---

### Post by justleen on 2010-06-25
> **complience said:**
> With two swaps, this means if you have two applications that require to use the swapspace they can both run concurrently. 

That is just plain wrong.. programs can write to disk concurrently, no need to create seperate partitions for each program. Your system will use multiple  swap partitions as one big swap space.

Plus, If your system is swapping, you load will run up anyway, so you should try to prevent swap usage anyway.

No program "requires" swap, your OS will use it when it runs out of real mem.

At post above: you can not split Primary partitions. Only Logical ones.
And a system can install on both logical and primary partitions.  its utter nonsense to state logical is better for data and primary for system,  en vice versa.

---

### Post by warfacegod on 2010-06-25
No need for two swap partitions, one will be fine. Hell, I don't even have one at all!

40 GB for the OS is quite allot. 15 GB is far more reasonable. I use 10 GB and none of my OS's has ever grown past 3.3 GB leaving 6.7 GB for /tmp use. Burning, etc.

What filesystem are you planning on using? I suggest ext4.

---

### Post by complience on 2010-06-25
You have two sticks of Memory, makes sense to me that you should have two swap areas.

Two swap areas on different disks perform better than one swap area with the equivalent amount of space. This allows interleaved swapping which means the swap areas are written to concurrently, minimizing diskhead movement, thus enhancing performance.

Thanks for the info wargodface, ill stick with 40gig to cover software bulk on future ubuntu releases - you never know.

Using Ext4

---

### Post by warfacegod on 2010-06-25
> Thanks for the info wargodface, ill stick with 40gig to cover software bulk on future ubuntu releases - you never know.

I don't foresee Ubuntu or it's software growing by 800% in the next oh ten years but hey, to each their own. You can always resize the partitions later if you feel the need. And that's warfacegod not wargodface. You must be thinking of someone else?!:biggrin: Who is he? I'll have to set him straight about pretending to be me...

---

### Post by justleen on 2010-06-25
Two swap areas on two _physical different_ disk will have a slight performace gain.
But, the OS will see one big swap partition!
It has absoluty nothing to do with how many sticks of memory you have, nothing at all!
 The swap mechanisn has no clue that is has two disks available. The only performance gain you will get when writing to swap is when the swap is occuring on the second disk - and only when the first disk happens to be used, and the second isnt, and then onl half the time.
Swap doesn't do "RAID"   or some or nifty balancing.

THe performance you gain using seperate disks is utterly lost against the simple fact that swapping in itself is slowing your system down.

A modern system should _**not**_ be swapping at all. If it is, fire up (h)top and check your IOwait. I'll wager an arm that is quite high at that stage.

---

### Post by dcstar on 2010-06-25
> **justleen said:**
> 
.........
The performance you gain using separate disks is utterly lost against the simple fact that swapping in itself is slowing your system down.

A modern system should _**not**_ be swapping at all. If it is, fire up (h)top and check your IOwait. I'll wager an arm that is quite high at that stage.

My god, someone who doesn't parrot the "Make your swap space twice your RAM and everything will be fine" myth!

And to the original question in this post, unless you are **sure** that you will never need more than 4 partitions on a disk, always use an Extended Partition before you run out of partition table entries.

I have a production server I have just taken over to maintain that the fool who originally partitioned it used all 4 Primary Partitions and now I cannot create a new partition to use the remaining 30% of space that is now needed without a lot of downtime and messing about.

---

### Post by complience on 2010-06-25
Thanks for the feedback guys, my ego is little bruised but i think my computer will be all the happier for it.

1 swap space it is.

---

### Post by warfacegod on 2010-06-25
If we have bruised your ego then I at least apologize. To make yourself feel better, find 3 people on the forum that need to be stopped from doing something that is clearly insane to their computer and talk them down from the ledge.:p

---

### Post by cascade9 on 2010-06-26
> **warfacegod said:**
> If we have bruised your ego then I at least apologize. To make yourself feel better, find 3 people on the forum that need to be stopped from doing something that is clearly insane to their computer and talk them down from the ledge.:p

I can help there......see, I've got this old ATI 9600XT, and I'm thinking about making it passive cooled with an old zalman northbridge cooler.....

---

### Post by warfacegod on 2010-06-26
That Zalman looks silly. I say you seal your computer to saltwater fish tank specs and fill it with non-electrically conductive liquid and mount dozens of those Zalmans to the case. That way it will be almost perfectly thermally conductive *and* it will look like some kind of demented electrobiomechanical fungal porcupine.

---

### Post by cascade9 on 2010-06-26
> **warfacegod said:**
> That Zalman looks silly.

Hey, I thought I disconnected that spy camera? 

Not MY fualt that the heatsink is blue and the card is red :P 

> **warfacegod said:**
>  I say you seal your computer to saltwater fish tank specs and fill it with non-electrically conductive liquid and mount dozens of those Zalmans to the case. That way it will be almost perfectly thermally conductive *and* it will look like some kind of demented electrobiomechanical fungal porcupine.

I've got some huge x-telco heatsinks, I'd use them. But no thanks on the oil cooling, seen it done, not my thing (and anyway, on my tester computers, I change something virutally every week)

*edit- hhmmm, 'virtually' might be the wrong word here. I actually do change something real in the testers most weeks.

---

### Post by warfacegod on 2010-06-26
> But no thanks on the oil cooling...

Then use regular, old fashioned water.

@ complience: If you are happy with the result of this thread, could you mark it as Solved under Thread Tools?

---

### Post by cascade9 on 2010-06-26
> **warfacegod said:**
> Then use regular, old fashioned water.

Seen that done as well,still not my thing.  As long as you use pure water, it runs OK for a while, but after a few months, the water has picked up enough junk from the computer parts that it starts to conduct. 

I'll stick with water in pipes. ;)

---

