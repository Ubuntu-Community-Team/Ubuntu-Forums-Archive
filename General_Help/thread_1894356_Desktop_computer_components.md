---
title: "Desktop computer components"
date: 2011-12-12
forum: General Help
---

### Post by edcv on 2011-12-12
Hi all,

I'm planing on building my own desktop computer which should last for a few years.
Currently I'm having trouble with finding some list of components or combinations of components that are working fine with Ubuntu.

My plan was first to use amd cpu (some fx type ) but then I see that all the available motherboards use realtek for ethernet and there seems to be some bug with it not working correctly. ( Correct me if I'm wrong? )
So I'm leaning towards intel i5 2500K and a Asus P8Z68-V PRO
Then I see multiple threads about this: [http://askubuntu.com/questions/86541/how-to-fix-boot-efi-not-ready](http://askubuntu.com/questions/86541/how-to-fix-boot-efi-not-ready)
and [http://ubuntuforums.org/showthread.php?t=1887174](http://ubuntuforums.org/showthread.php?t=1887174)

So my question is if you have any suggestions or could just post your own components and if they function well ( as win is not an option and I don't want to end up with an expensive machine that I can't use ).

I guess this list could be useful for others that are planing on buying a computer.

Tl;dr Do you have a new desktop computer components that are working fine with ubuntu 11.10? please share your setup.


Cheers!

---

### Post by coffeecat on 2011-12-12
> **edcv said:**
> My plan was first to use amd cpu (some fx type ) but then I see that all the available motherboards use realtek for ethernet and there seems to be some bug with it not working correctly. ( Correct me if I'm wrong? )

I'm posting from my main desktop machine which runs Natty and Oneiric just fine. AMD CPU and:

```
$ lspci | grep -i ethernet
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

If the Realtek ethernet wasn't working in Oneiric I wouldn't be able to post! :wink:

Perhaps some other Realtek chipsets are problematic. Where did you read about this possible bug?

---

### Post by edcv on 2011-12-12
For the realtek see:
See here:[http://ubuntuforums.org/archive/index.php/t-1850683.html](http://ubuntuforums.org/archive/index.php/t-1850683.html)
and here:
[http://phoronix.com/forums/showthread.php?60433-Gigabyte-GA-990FXA-UD3-for-Ubuntu](http://phoronix.com/forums/showthread.php?60433-Gigabyte-GA-990FXA-UD3-for-Ubuntu)

What mb do you have?

---

### Post by coffeecat on 2011-12-12
> **edcv said:**
> For the realtek see:
See here:[http://ubuntuforums.org/archive/index.php/t-1850683.html](http://ubuntuforums.org/archive/index.php/t-1850683.html)
and here:
[http://phoronix.com/forums/showthread.php?60433-Gigabyte-GA-990FXA-UD3-for-Ubuntu](http://phoronix.com/forums/showthread.php?60433-Gigabyte-GA-990FXA-UD3-for-Ubuntu)

I can't see anything relevant to Realtek in the first link. In the second link "pony-tail" in October 2011 makes a vague statement about a "known issue" with Realtek in Ubuntu, but then refers to an Ubuntuforums thread from **3 years ago** to support this statement! The 2008 thread is about the same Realtek chipset as mine, but the OP was using Ubuntu 8.10.

Newer version of Ubuntu = newer kernel = newer r8169 driver.
 
> **edcv said:**
> What mb do you have?

Asus M4A78LT-M with AMD Athlon(tm) II X4 640 CPU. The onboard graphics is unrewarding so I use an ATI Radeon HD 5450 PCIe card. Works just fine with the default open source driver in both Natty and Oneiric.

---

### Post by edcv on 2011-12-12
> **coffeecat said:**
> I can't see anything relevant to Realtek in the first link. In the second link "pony-tail" in October 2011 makes a vague statement about a "known issue" with Realtek in Ubuntu, but then refers to an Ubuntuforums thread from **3 years ago** to support this statement! The 2008 thread is about the same Realtek chipset as mine, but the OP was using Ubuntu 8.10.

Newer version of Ubuntu = newer kernel = newer r8169 driver.
 


Asus M4A78LT-M with AMD Athlon(tm) II X4 640 CPU. The onboard graphics is unrewarding so I use an ATI Radeon HD 5450 PCIe card. Works just fine with the default open source driver in both Natty and Oneiric.

Sorry for not being very clear, the first link refers to a motherboard having realtek 8111E.
Here are some other links: [http://ubuntuforums.org/showthread.php?t=1865328](http://ubuntuforums.org/showthread.php?t=1865328)
But seems to be some solution here: [http://ubuntuforums.org/showthread.php?t=1855441&page=4](http://ubuntuforums.org/showthread.php?t=1855441&page=4)
Maybe nothing to worry about......

---

### Post by coffeecat on 2011-12-12
Well - that's very interesting. I'm simply not having the issues those  posters are describing, even though the command suggested in this post:

[http://ubuntuforums.org/showpost.php?p=11339160&postcount=3](http://ubuntuforums.org/showpost.php?p=11339160&postcount=3)

Returns the same 10ec:8168 as described.

```
$ lspci -nnk | grep -iA2 net 
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169
```

Only one thing I can think of. The card is a gigabit one, but I'm running it at less than gigabit speeds, in fact less than 100Mbps. I don't know whether my router is capable of gigabit speeds, but my ethernet speed is limited by the ethernet over mains devices I am using. They are rated at 85Mbps, but in practice I get about 60. Which is far more than I need anyway. Perhaps the people with problems are trying to get gigabit ethernet.

**EDIT**: just checked out my router specs. It only supports fast ethernet (100 Mbps) so I can't test whether gigabit ethernet is the problem here.

---

### Post by kurt18947 on 2011-12-12
I too have a Realtek ethernet chip on an AMD processor/AMD chipset Gigabyte Motherboard.  No issues except with booting a live USB stick when the stick was not formatted with Windows. I'm pretty sure that's a BIOS issue, not a chipset issue.  Some RealTek *wireless* network adapters using the RTL8188 chipset can be problematic based on posts in networking & wireless.

---

### Post by edcv on 2011-12-12
Yeah, well if it becomes a problem then in worst case scenario I can buy a pcie lancard.
Want to buy an amd instead of intel and spend the difference on a ssd.
Should 64gb be enough for everything except /home ?

---

### Post by oldtimer7777 on 2011-12-12
> **edcv said:**
> Yeah, well if it becomes a problem then in worst case scenario I can buy a pcie lancard.
Want to buy an amd instead of intel and spend the difference on a ssd.
Should 64gb be enough for everything except /home ?

If you are going to build an AMD desktop computer, make sure you stick with Nvidia Graphics cards, not ATI.  That would also be some good advice.

---

### Post by edcv on 2011-12-12
> **oldtimer7777 said:**
> If you are going to build an AMD desktop computer, make sure you stick with Nvidia Graphics cards, not ATI.  That would also be some good advice.

Thanks for the tip.
I will not be using it for gaming much, more for cad related stuff. 
You have not had any issues with nvidia and blender or something similar: 
[http://www.tomshardware.co.uk/forum/311779-15-does-suffer-opengl-issues-series](http://www.tomshardware.co.uk/forum/311779-15-does-suffer-opengl-issues-series)

---

### Post by oldtimer7777 on 2011-12-12
> **edcv said:**
> Thanks for the tip.
I will not be using it for gaming much, more for cad related stuff. 
You have not had any issues with nvidia and blender or something similar: 
[http://www.tomshardware.co.uk/forum/311779-15-does-suffer-opengl-issues-series](http://www.tomshardware.co.uk/forum/311779-15-does-suffer-opengl-issues-series)

A better question would be to ask which Nvidia card works best for what you are trying to do.

Do you want to use Blender? Are you going to use it? 

There are more problems and issues with ATI cards then you will ever find with Nvidia cards.

Don't force incompatible hardware to work with Ubuntu, that would be the worst approach to building your own custom desktop computer, from my experience, with the Ubuntu operating system.  That is my best suggestion for you.

---

### Post by edcv on 2011-12-13
I use similar software to Blender, e.g. paraview, ensight.
Something you would recommend that is not extremely expensive?

---

