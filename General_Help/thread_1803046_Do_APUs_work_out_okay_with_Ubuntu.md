---
title: "Do APUs work out okay with Ubuntu?"
date: 2011-07-12
forum: General Help
---

### Post by linuxuser12345 on 2011-07-12
I am thinking of creating a new system running Ubuntu, but I saw the new AMD APUs (accelerated processing units) that they are selling, that combines the CPU and the GPU in one. I am thinking of getting one of these instead of a traditional processor and GPU, but I need to know something: Will it work okay with Ubuntu? Are AMDs drivers for these new APUs capable of running correctly on Ubuntu?

Also, what would you recommend: Getting a traditional AM3+ motherboard, processor, and Nvidia-powered GPU, or get the new thing with an FM1 motherboard + an APU? I am looking for a system that will run super-stable with Ubuntu and also last a *long* time.


[If anyone is interested, you can take a look at these new APUs [here]("http://promotions.newegg.com/AMD/11-1834/index.html?cm_sp=SubCat_Processors-Desktops-_-AMD/11-1834-_-http%3a%2f%2fpromotions.newegg.com%2fAMD%2f11-1834%2f478x88.jpg").]

---

### Post by seawolf167 on 2011-07-12
From what I'm aware of, the [AMD Fusion APUs ]("http://sites.amd.com/us/fusion/apu/Pages/fusion.aspx")work for the most part, but require some configuration tweaking to get everything working as [perfectly/well] as possible. Give the linux kernel & Ubuntu distro another couple months; so maybe 11.10 and it will [IMO] probably work out-of-the-box.

---

### Post by linuxuser12345 on 2011-07-12
So, I should probably go with a standard AM3+ processor and motherboard + an Nvidia graphics card? I heard Nvidia is the best for Linux, anyways

---

### Post by seawolf167 on 2011-07-12
I would have said one over another a couple years ago, but both Nvidia & ATI cards have pretty good driver support. You can either install them through the "Additional Drivers" program or by installing the proprietary driver suite directly from the manufacturer. Your restriction in the video card category is now more a question of "how much do I want to pay?" vs. "which card has better *nix support/drivers?"

---

### Post by pqwoerituytrueiwoq on 2011-07-12
if you are willing to wait a little or while (month or two) you could get get a better price when AMD gets its new 8 core cpu out the door

---

### Post by linuxuser12345 on 2011-07-13
What do you think is better/faster: An AMD A8-3850 2.9GHz APU (Quad-core), or an AMD Phenom II X4 @3.0 GHz + a Nvidia GeForce 8400 GS 512MB?

---

### Post by seawolf167 on 2011-07-13
> **linuxuser12345 said:**
> What do you think is better/faster: An AMD A8-3850 2.9GHz APU (Quad-core), or an AMD Phenom II X4 @3.0 GHz + a Nvidia GeForce 8400 GS 512MB?

I'd see if there are any benchmarks out there for the APU. I'm not sure on that data. Though if you get something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115211") you can overclock it to 4+ Ghz. I'm an Intel kind-of-guy for the headroom they have built in for overclocking.

---

### Post by mcduck on 2011-07-13
> **linuxuser12345 said:**
> I am thinking of creating a new system running Ubuntu, but I saw the new AMD APUs (accelerated processing units) that they are selling, that combines the CPU and the GPU in one. I am thinking of getting one of these instead of a traditional processor and GPU, but I need to know something: Will it work okay with Ubuntu? Are AMDs drivers for these new APUs capable of running correctly on Ubuntu?

Also, what would you recommend: Getting a traditional AM3+ motherboard, processor, and Nvidia-powered GPU, or get the new thing with an FM1 motherboard + an APU? I am looking for a system that will run super-stable with Ubuntu and also last a *long* time.


[If anyone is interested, you can take a look at these new APUs [here]("http://promotions.newegg.com/AMD/11-1834/index.html?cm_sp=SubCat_Processors-Desktops-_-AMD/11-1834-_-http%3a%2f%2fpromotions.newegg.com%2fAMD%2f11-1834%2f478x88.jpg").]
The new Llano-family APUs should work just fine with Linux (and Ubuntu).

Actually here's a Phoronix benchmark of A8-3500M, tested on Ubuntu 11.04: [http://www.phoronix.com/scan.php?page=article&item=amd_llano_linux&num=1]("http://www.phoronix.com/scan.php?page=article&item=amd_llano_linux&num=1")

---

### Post by linuxuser12345 on 2011-07-13
Yeah, but I don't want to spend $260 for a processor. :/

---

### Post by linuxuser12345 on 2011-07-13
Will the APU work okay under Ubuntu 10.04 LTS?

---

### Post by steve7777777 on 2011-07-15
Full disclosure -- I like AMD processors, and build all of my own systems. I want Bulldozer, the next generation of AMD processors to succeed. From what I've been reading Bulldozer may be delayed until 2012, so I think saying it will be out in a "couple months" is overly optimistic. This sucks for me because my one of my PC's has a wonky motherboard - slowly dying, some of the SATA ports are bad and I'd like nothing more than to toss it and replace with Bulldozer. Llano A8-3850 is an excellent alternative and available right now. Only thing is I'd prefer to wait for the second revisions of the motherboards, and also for additional confirmation that it works perfectly with Ubuntu with a standard installation.

The A8-3850 has low idle power, and seems to be a nice CPU for a server that will be on 24x7 and still powerful enough for 1080p h264 video, virtual machines, etc.

BTW if you want to go with the proven Phenom II or Athlon II, this is a nice mb - [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128444](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128444). ATX, not Micro ATX but very solid and stable with Ubuntu.

---

### Post by fezzik on 2011-07-15
I have been looking at the APU's as well.  I actually came here because I was looking at the same thing.  Since it appears that it will work fine here is my 2 cents.  

I would say that it depends on what you are doing.  The APU processors have what they say is the equivalent of an ATI 6550 video card but that the information would get to where it is going faster because it doesn't have to travel a few extra inches of circuitry.  I haven't yet had the opportunity to real world test these but from what I have seen and the research I have done so far.  I would say that if you do a lot of speed intensive processing like games or video editing or streaming then the APU has its advantages.  It simplifies the process and removes some unnecessary bottlenecks.  It has a perfectly capable processor and some new and improved software to help take advantage of the chip more fully.  Also the Powernow (trying from memory so I may have the name wrong) is a new more advanced version from what the Athlon and Phenom processors have.  From what I have read and heard it is supposed to have better management and power down the cores that aren't being used and up the ones that are to real time usage.  

The APU has higher L2 Cache than the AthlonII processors.  The Phenom has the same L2 Cache as the AthlonII but adds a L3 Cache which is generally higher than the APU's L2 cache.  L2 Cache is faster than L3 cache so there may not actually be a big performance difference but real world I would be interested in seeing the difference.  

I am considering re-doing my computer with an APU and a Hybrid disk drive for the OS.

---

