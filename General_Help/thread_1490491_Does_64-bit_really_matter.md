---
title: "Does 64-bit really matter?"
date: 2010-05-22
forum: General Help
---

### Post by jinba.ittai on 2010-05-22
Now that i signed up in the forums, i think i will just downgrade to a later version of ubuntu seeing as there is alot of problems with 10.04

My original problem is i installed 32-bit on my amd 64 bit pc, and its running epically slow. Just downloaded the 64-bit but havent installed it yet. I was wondering if installing the 64 bit would fix the glitchiness or what not, before i back up all 469gb of data again (which takes around 5 hours!!) and reinstall ubuntu.

any suggestions?

btw:
Emachines T6412
512 mb ram ddr
amd 64 bit

(soon i will upgrade to 4 gigs or ram, then a new mobo, then a new case! this is just a play around computer)

---

### Post by Lucky. on 2010-05-22
Hmm, that's odd.  I don't know why 32 bit would run that slow, but I suppose it wouldn't hurt to try 64.  I wouldn't be too optimistic on 64 running that much faster though.

Sorry man, I hope things work out.

---

### Post by philinux on 2010-05-22
One suggestion is to have home on it's own partition and/or a data partition. Reinstalling is dead easy then.

---

### Post by jinba.ittai on 2010-05-22
Im not too worried about it. My next pay check ill be upgrading alot of the hardware. All of the crap thats on this pc at the moment might be the reason its running slow. But i just wondered if it may be the difference between running 64bit or 32bit. 

The hard drives (2 of them) are still ide, which is pretty old. So next week ima go pick up a couple 1tb sata drives. (only $70!! Stuffs getting cheap!)
and maybe 1 gb of ram, that crap is expensive. 

If it still runs slow then ill know for sure its the software instead of the hard ware. (or maybe the mobo?)

---

### Post by jinba.ittai on 2010-05-22
> **philinux said:**
> One suggestion is to have home on it's own partition and/or a data partition. Reinstalling is dead easy then.

And how may i do that?

---

### Post by tuX9th on 2010-05-22
I don't think that the 64bit version will be faster. It could be slower. The biggest adavantage of 64 bit is that you can manage more than 4gb ram.
just read through the wikipedia article.

---

### Post by jerome1232 on 2010-05-22
At 512 MB's of ram I wouldn't go 64 bit, it has a slightly larger memory footprint than 32 bit does.

When you get that 1 GB of ram, maybe go 64 bit.

edited: I missread a post.

---

### Post by jinba.ittai on 2010-05-22
> **jerome1232 said:**
> At 512 MB's of ram I wouldn't go 64 bit, it has a slightly larger memory footprint than 32 bit does.

When you get that 1 GB of ram, maybe go 64 bit.

edited: I missread a post.

Definitely will do! Thanks!

---

### Post by jinba.ittai on 2010-05-22
Does anyone have any clue as to why it might be running slow or glitchy? 

runs fine on my laptop and dell desktop. now im almost sure it might be hard ware.

would an old hard drive be the problem? 
i know ram would speed it up but its glitchy when opening programs, like it doesnt know where to find the data

---

### Post by cascade9 on 2010-05-22
With an AMD 3400+, you shouldnt be lacking any CPU power. I think that it would be the video card (ATI X200, intergraded). Your RAM level isnt helping either...  

> **Sandy V Jina said:**
> And how may i do that?

Its one of the options when you setup the drive. QWhen you get to 'perpare disk space' click 'specifiy partitions manually'. You will need 10GB (approx) for /root, /home whatever you want. (and if you decde to make any other partitions, the size can also be whatever you want). Dont forget a swap partition ;)

---

### Post by Muskegman on 2010-05-22
I wouldnt bother installing a 64bit OS with only 512mb of ram it would be pointless as 512mb is not much ram. 

After you have upgraded your ram. motherboard etc then yes install the 64bit OS , as long as your new motherboard chipset is 64 bit capable.

Having 4gigs of ram or more will make a big difference with switching to 64 bit and it will take full advantage of the extra ram you have and performance will be much much better.

After upgrading your ram to 4gigs, I would just try the 32 bit OS first , you will find a huge difference in speed and performance after upgrading from only 512mb.

---

### Post by jinba.ittai on 2010-05-22
> **cascade9 said:**
> With an AMD 3400+, you shouldnt be lacking any CPU power. I think that it would be the video card (ATI X200, intergraded). Your RAM level isnt helping either...  



Its one of the options when you setup the drive. QWhen you get to 'perpare disk space' click 'specifiy partitions manually'. You will need 10GB (approx) for /root, /home whatever you want. (and if you decde to make any other partitions, the size can also be whatever you want). Dont forget a swap partition ;)

Thanks, ill be sure to read back on this next week when i upgrade some of the parts. Guess ill dish out 80 bucks for a graphics card as well. Good thing this pc has pci express

---

### Post by jinba.ittai on 2010-05-22
Thanks to all of you for helping me! I guess we wont see any real results until i upgrade. 

All of this was really helpful info!

---

### Post by cascade9 on 2010-05-22
If you dont play games, but do watch media, the most expensive card I would get is a nVidia GT220 (from about $50-55 US). Anything more is a waste. 

If you dont use the computer to watch video, then even a lowly 8400GS (from about $30 US) will be more than enough ;)

---

### Post by jinba.ittai on 2010-05-22
> **cascade9 said:**
> If you dont play games, but do watch media, the most expensive card I would get is a nVidia GT220 (from about $50-55 US). Anything more is a waste. 

If you dont use the computer to watch video, then even a lowly 8400GS (from about $30 US) will be more than enough ;)

Well, i do know the graphic card also takes load off the cpu,giving you more power, so i will most likely get something between 50-80. those cards are getting pretty cheap as well.

---

### Post by philinux on 2010-05-22
> **Sandy V Jina said:**
> And how may i do that?

During the install choose manual partitioning.

/ needs about 10 or 12 gig.
swap = ram if you hibernate.
/home can be all the rest or smaller if you want another data partition.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by jerome1232 on 2010-05-22
It's hard to tell what your bottleneck is, you really need to take a look at some performance tools and see what's going on.

Install htop, or us top, check the cpu load, the ram usage, are you swapping alot?

I have a suspicion it's your ram, integrated graphics is probably stealing some it for it's use so you are really running with less than 512. In my experience 512 is barely adequate for gnome and actually doing stuff.

---

### Post by jinba.ittai on 2010-05-22
> **jerome1232 said:**
> It's hard to tell what your bottleneck is, you really need to take a look at some performance tools and see what's going on.

Install htop, or us top, check the cpu load, the ram usage, are you swapping alot?

I have a suspicion it's your ram, integrated graphics is probably stealing some it for it's use so you are really running with less than 512. In my experience 512 is barely adequate for gnome and actually doing stuff.

[IMG]http://i48.tinypic.com/zx9w6u.png[/IMG]

CPU % is bouncing between 10-70%

---

### Post by jerome1232 on 2010-05-22
Yeah your running with 396 MB's of ram, I *think* that 1 GB stick will make a world of difference.

This is imo of course.

---

### Post by jinba.ittai on 2010-05-23
> **jerome1232 said:**
> Yeah your running with 396 MB's of ram, I *think* that 1 GB stick will make a world of difference.

This is imo of course.

Just got some extra money, gona get some ram tomorow, well today. well in a few hoours (pulled an all nighter doing some work)

---

### Post by cascade9 on 2010-05-23
> **Sandy V Jina said:**
> Well, i do know the graphic card also takes load off the cpu,giving you more power, so i will most likely get something between 50-80. those cards are getting pretty cheap as well.

The faster video cards will only help if your playing games, doing hardware video decoding and (some) graphics/rendering programs. Well, desktop effects will also use GPU power (to some degree) but once you are past a certain point  they dont help there either. The GT240 (next model up from the GT220) doesnt use VDPAU (nvidia hardware video decoding) any more than a GT220. 

Then again, $50-80 could well be a GT220, or even a GT210, depending on how expensive the computer shop you are going to is.

---

### Post by jerome1232 on 2010-05-23
I know I got my GT210 off of tiger direct for like $19.99, thought that was a pretty good price.

---

