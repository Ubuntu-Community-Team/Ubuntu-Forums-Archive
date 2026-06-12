---
title: "Ubuntu and AMD Radeon HD 7500g"
date: 2012-10-06
forum: General Help
---

### Post by NathanChung on 2012-10-06
Hi, I'm new to this whole Linux thing but I would really love giving it a shot. I will be the first to admit that I am no expert when it comes to computers. However, I do manage to generally find the information I need via the internet, but not this one. Thus, I would like to ask the Ubuntu community some questions before I make the complete switch over to Ubuntu.

There are many reasons why I wanted to try out Ubuntu. I love how viruses can't really affect it and I love the speed boost it has over a windows OS. Nevertheless, the main reason I want to try out Ubuntu is for all of the beautiful aesthetic it comes packaged with. The "Cube" and all of those amazing effects are just incredible. However, I have been having a problem in trying to use these effects.

Let me begin by saying what kind of computer I have. I have the [Hp Envy 6]("http://www.bestbuy.ca/en-CA/product/hewlett-packard-hp-envy-15-6-laptop-featuring-amd-a6-4400m-processor-6-1048ca-black-envy-6-1048ca/10208053.aspx"). It has an AMD processor and an AMD Graphics Card. According to the main site at Help.Ubuntu.com, AMD/ATI graphics cards seem to have issues with Ubuntu. I've also read that to utilize visual effects, my graphic card needs to be able to have "3d support". I followed the instructions on [https://help.ubuntu.com/community/CompositeManager/](https://help.ubuntu.com/community/CompositeManager/)
to try and get the cube to work. However, it either did not activate or it does not work on my laptop. Another thing I should say is that I was on the "Try Ubuntu first" setting from my USB stick. I'm not sure if that makes any difference. I really just wanted to make sure that everything I wanted to use Ubuntu for was going to be working before I actually installed it. Anyways, these are the questions I have.

How can I check if my graphics card has 3d Support?

If I can't utilize the cube, what other functionalities will I be unable to use because of my graphics card?

Do I have to install Ubuntu before I can really "test" it out? As in download programs and do updates?

I heard of a program called "[AMD Catalyst™ Proprietary Display Driver - Linux x86 & Linux x86_64]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")" Will that fix my problem?

if I wanted to utilize Ubuntu a lot more then Windows 7 (while on a dual boot) how should I separate the drives? What is the minimum amount I can leave windows 7 at?

---

### Post by 3rdalbum on 2012-10-06
Newer Radeon HD graphics chips like yours work fine in Ubuntu with the proprietary ATI driver. All you need to do is install Ubuntu, and then run the Hardware Drivers program and it will offer to install the correct driver for you.

The live CD which you are using does not have the driver already loaded, and that's why you can't get any special graphical effects. Once you've installed Ubuntu you can also install the driver as above and activate the graphical effects. Just be very careful as the Cube code is very old, and doesn't work well on today's systems.

Don't download the driver from the AMD website; you can get the same driver a lot easier from the Hardware Drivers program in Ubuntu.

As for your last question, you should allow 10 gigabytes for the system and programs, plus as much disk space as you have RAM, and then however much home directory space you're going to use.

So, for instance:

I have four gigabytes of RAM.
I will probably use 32 gigabytes of disk space for personal documents
I already know that ten gigabytes is enough for Ubuntu plus the programs I'll want and need, with still some space left over

4+32+10 = 46 gigabytes to allocate to the Ubuntu part of the hard disk.

You may want to allow more than that for your personal files. Perhaps 100 gigs would be good round figure for allocating to Ubuntu and all your documents.

---

### Post by NathanChung on 2012-10-06
> **3rdalbum said:**
> Newer Radeon HD graphics chips like yours work fine in Ubuntu with the proprietary ATI driver. All you need to do is install Ubuntu, and then run the Hardware Drivers program and it will offer to install the correct driver for you.

The live CD which you are using does not have the driver already loaded, and that's why you can't get any special graphical effects. Once you've installed Ubuntu you can also install the driver as above and activate the graphical effects. Just be very careful as the Cube code is very old, and doesn't work well on today's systems.

Don't download the driver from the AMD website; you can get the same driver a lot easier from the Hardware Drivers program in Ubuntu.

As for your last question, you should allow 10 gigabytes for the system and programs, plus as much disk space as you have RAM, and then however much home directory space you're going to use.

So, for instance:

I have four gigabytes of RAM.
I will probably use 32 gigabytes of disk space for personal documents
I already know that ten gigabytes is enough for Ubuntu plus the programs I'll want and need, with still some space left over

4+32+10 = 46 gigabytes to allocate to the Ubuntu part of the hard disk.

You may want to allow more than that for your personal files. Perhaps 100 gigs would be good round figure for allocating to Ubuntu and all your documents.

I guess it's true about how they say the Ubuntu community is extremely helpful! I thank you!

---

### Post by pompel9 on 2013-04-05
I have this graphics card too. But under proprietary drivers it states that: Advanced Micro devices [AMD] nee ATI: unknown.

I have all the latest updates, and I am on Ubuntu 12.10 with standard linux kernel

---

