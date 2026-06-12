---
title: "A few questions from a noob"
date: 2012-02-04
forum: General Help
---

### Post by LLCoolJeff on 2012-02-04
First of all, from your experience am I better off buying a standard windows laptop like a dell,  or getting something like a system76? Is there really much difference between the two?

Secondly, is virtualbox pretty reliable? Assuming that it is up and running correctly with windows 7, would it be able to run all windows 7 native applications from "within" ubuntu? Would it be better to use virtualbox, or just keep a bootable version of windows on the hd?

[EDIT] ^^^^Of course I mean using virtualbox, or a windows installation for those moments when WINE will not work for me./

Thirdly, I am pretty new to linux, so I'm a bit unsure as to exactly how much laptop I need. My mediocre gateway nv52 from '09 is running like a champ with ubuntu 10.04 x64, but I am sensing it is about to go so I am in the market for a new one. I mainly use my computer for recording and mixing music,  and watching movies, and such. More like an entertainment center than anything else. Any advice on what company to go with to take care of my computer needs?

Thanks for reading, I know its a lot of questions, but I think I should have a pretty good idea of what I need with just a little advice.

---

### Post by rajan on 2012-02-04
In general, HP and Intel both support linux fairly well, and I've had video card problems with both Nvidia and ATI. 

If you're interested in getting away from Windows, you probably should keep a partition on your HD with OS 7 just in case. It's really easy to set up the side-by-side partitions -- basically all you do is (in Windows) shrink the size of the windows partition, then pop in your install CD and install Ubuntu on the newly-created empty space. From my experience reading how to do this on the web, it's easier to start with a windows installation and install an ubuntu partition than the other way around. 

I think the only people that really miss windows are the gamers who can't get WoW or whatever on linux. 

Lastly, in terms of specifics on hardware, if you find something you really like, google the model number and see if there are lots of problems with it and linux working together. I never have the foresight to do that, but I always wish I did.

---

### Post by LLCoolJeff on 2012-02-04
Nice, I came to the conclusion that HP pretty much had the best deals for the money anyway. So I will probably be getting an HP when I get the chance. 

Now is there any disadvantage to setting up a partition with linux, is it going to slow it down at all haveing windows on another parition? That is how I have it setup now, I just want to make sure that in the future it won't inhibit my new system in any way.

---

### Post by rajan on 2012-02-05
> **LLCoolJeff said:**
> 
Now is there any disadvantage to setting up a partition with linux, is it going to slow it down at all haveing windows on another parition? That is how I have it setup now, I just want to make sure that in the future it won't inhibit my new system in any way.

There's no difference I can think of between having ubuntu/windows on the same HD versus having them on two separate HDs. In other words, once you're past the bootloader, the OSs don't interact. 

The only thing you have to be careful to remember is that MS doesn't play well with others, and that you should not alter the windows partitions routinely from ubuntu. I haven't had any problems transferring data from the MS partition to the ubuntu partition, but the reverse occasionally causes problems. In addition, your worst-case scenario is one where MS's boot loader somehow ruins ubuntu's GRUB, and at that point you will be glad you back up regularly. This isn't common, but it will certainly happen to you at the worst possible time.

---

### Post by mastablasta on 2012-02-05
careful with HP as some of their computers have dual graphics. this GPU switching is not supported in linux. at leats not well.
However you could get an HP with Linux on it and then overwrite that with Ubuntu and add windows if necessary.

---

### Post by Bucky Ball on 2012-02-05
> **LLCoolJeff said:**
> 

Now is there any disadvantage to setting up a partition with linux, is it going to slow it down at all haveing windows on another parition?

Makes no difference whatever. You only have one OS running at once. Think of it this way: If you had one operating system would it slow you down by having a separate data partition???? Actually, probably miniscule as that partition would be in use and mounted whereas using Windows, the Linux partition will not be mounted and may as well not be there. As for using Linux you can permanently unmount the Win partition for the same effect.

---

### Post by jwbrase on 2012-02-05
> **LLCoolJeff said:**
> First of all, from your experience am I better off buying a standard windows laptop like a dell,  or getting something like a system76? Is there really much difference between the two?

I myself am very happy with my System76 machine. It's been running strong for two and a half years now. System76 machines are a bit expensive, however, and don't come with Windows, so you'd have to buy Windows separately, and it's more expensive that way. I bought my System76 machine because I didn't want to give any money to Microsoft, and felt I could survive without Windows (which I've managed quite well), so the "must buy Windows separately" thing was moot. If you feel you can live without Windows, I'd highly recommend System76, but if not, it would be better to go with a manufacturer that sells it pre-installed. (In general, any OS will give you much less hassle if you buy a machine with it pre-installed than if you install it yourself, and for proprietary OS's it's also usually the cheaper way to go).

---

