---
title: "Changing grub default"
date: 2010-07-08
forum: General Help
---

### Post by Total Noob on 2010-07-08
I'm using 7.4, which means no built in Startupmanager and none in the repository.

I'm looking to switch the default setting in the Grub to a different OS and to add more time to choose.

Can someone walk me through the terminal session that does that?

Thanks.

---

### Post by philinux on 2010-07-08
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

To here.
 
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

However, [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases), you are running an End Of Life release which is not supported anymore.

---

### Post by Total Noob on 2010-07-08
> **philinux said:**
> [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

To here.
 
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

However, [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases), you are running an End Of Life release which is not supported anymore.

Thanks. The second one was the winner; the first one is for Karmic, which I guess is 5 editions later than mine.

I use an obsolete version b/c my computer is a P2 with 500 Mhz and about 400 MB Ram, and later editions overpowered slightly more powerful computers that I have, and seem to need at least a P4 with 1 Gig of processing power and 1 Gig of Ram. I hope I'm not facing any severe security problems.

---

### Post by QLee on 2010-07-08
[QUOTE=Total Noob]... I hope I'm not facing any severe security problems.[/QUOTE]

Well, looking at your choice of username, I want to suggest that perhaps you are. A no longer supported version will not be getting any security updates, thus anything identified after end of life date won't be patched. That might work fine, depending how you use your system, for a while or even a long while if you don't use anything that has been cracked but the problem is that you can no longer rely on the Ubuntu maintainers to protect you. Kind of defeats the purpose of secure repositories and package managers that handle security upgrades for you. I can't recommend this for a "total noob", but you are free to use you system as you see fit, you probably don't keep anything you want to be secret on it anyway.

---

### Post by philinux on 2010-07-08
> **Total Noob said:**
> Thanks. The second one was the winner; the first one is for Karmic, which I guess is 5 editions later than mine.

I use an obsolete version b/c my computer is a P2 with 500 Mhz and about 400 MB Ram, and later editions overpowered slightly more powerful computers that I have, and seem to need at least a P4 with 1 Gig of processing power and 1 Gig of Ram. I hope I'm not facing any severe security problems.

This maybe better then.

[http://peppermintos.com/about-peppermint/](http://peppermintos.com/about-peppermint/)

---

### Post by Total Noob on 2010-07-08
> **QLee said:**
> Well, looking at your choice of username, I want to suggest that perhaps you are.

You have me pegged. As for Peppermint, the system requirements are 

> i386 or derivative processor (AMD64 and x86_64 are fine as well)

Is a Pentium 2 an i386? How about P3, P4 and Celeron M, which are in other computers I use home and work. 

I'm a little boggled by the x86 and x64 terminology, I guess it has something to do with the processing chips, but I don't know what this stuff really means. This stuff always appears without any elaboration at Linux websites, and is a headache to non-IT end users.

Thanks.

---

### Post by MCSE_Crossover on 2010-07-08
> **Total Noob said:**
> You have me pegged. As for Peppermint, the system requirements are 



Is a Pentium 2 an i386? How about P3, P4 and Celeron M, which are in other computers I use home and work. 

I'm a little boggled by the x86 and x64 terminology, I guess it has something to do with the processing chips, but I don't know what this stuff really means. This stuff always appears without any elaboration at Linux websites, and is a headache to non-IT end users.

Thanks.

Yes, i386 just makes a reference to the original 32-bit Pentium chip introduced in the mid-80's. Now, it is commonly referred to either x86 or x64, which references either 32-bit or 64-bit, respectively. You should be fine as long as you meet the RAM requirements.

---

### Post by Total Noob on 2010-07-08
> Yes, i386 just makes a reference to the original 32-bit Pentium chip introduced in the mid-80's. Now, it is commonly referred to either x86 or x64, which references either 32-bit or 64-bit, respectively. You should be fine as long as you meet the RAM requirements.

I ask because there was a little blurb in this blog that said Canonical was recommending one version of 10.4 for 32 bit desktops and a different one for 64 bit desktops, and I wonder whether I chose unwisely for my other old computer leaving it overmatched.

Is there a specific way to tell what chips are 32's and which are 64's from the control panel or otherwise?

Thanks.

---

### Post by QLee on 2010-07-08
[QUOTE=Total Noob]I ask because there was a little blurb in this blog that said Canonical was recommending one version of 10.4 for 32 bit desktops and a different one for 64 bit desktops, and I wonder whether I chose unwisely for my other old computer leaving it overmatched.[/QUOTE]

Which blog are you writing about?

All of the chips you have mentioned above are 32bit

What do you think would happen if you tried to install a 64bit Ubuntu to a 32bit computer?

[QUOTE=Total Noob]Is there a specific way to tell what chips are 32's and which are 64's from the control panel or otherwise?.[/QUOTE]

I google the chip if I am unsure, note that the 64bit CPU has not been mainstream for very long, you aren't likely to find it in an old computer.

---

### Post by Total Noob on 2010-07-08
> **QLee said:**
> Which blog are you writing about?

[http://ubuntuforums.org/showthread.php?t=1526391&highlight=canonical+in+print](http://ubuntuforums.org/showthread.php?t=1526391&highlight=canonical+in+print)

> **QLee said:**
> What do you think would happen if you tried to install a 64bit Ubuntu to a 32bit computer?

Didn't know it was something to worry about.

> **QLee said:**
> I google the chip if I am unsure, note that the 64bit CPU has not been mainstream for very long, you aren't likely to find it in an old computer.

Since I didn't know about this stuff, I didn't know to do that due diligence.  The download instructions were vague or nonexistent when accessing the iso from the Distrowatch directly. Also, I upgraded to 10.4 on an old computer due to nagware, and I'm not sure what the upgrade was; the maker did not provide a lot of instructions about that process, so I don't konw whether the upgrade was to the 64 or 32 version.

Thanks for letting me know to keep an eye out for this stuff, but we blissfully ignorant noobs aren't getting enough plain English instructions from teh distributors to make smart choices.

---

### Post by MCSE_Crossover on 2010-07-08
The bottom line is that you have either 32-bit or 64-bit architecture these days when it comes to processors. Any newer processor that you buy these days from Dell or some other company is more than likely going to be a 64-bit architecture. But, it is capable of running either a 32-bit or a 64-bit operating system. The same is not true the other way around. 32-bit processors (architecture) will not run a 64-bit Operating System. Unless you have more than 4GB of RAM or a need to have 64-bit architecture, stick with 32bit. That will be fine and will certainly eliminate some of the other looming buggy issues that come with some of the 64-bit systems.

---

### Post by QLee on 2010-07-08
[QUOTE=MCSE_Crossover]Yes, i386 just makes a reference to the original 32-bit Pentium chip introduced in the mid-80's. Now, it is commonly referred to either x86 or x64, which references either 32-bit or 64-bit, respectively. You should be fine as long as you meet the RAM requirements.[/QUOTE]

Just to correct this, the 386 and 486 preceeded the pentium, Intel decided to use "pentium" instead of 586 but yes it is the 386 line of CPU that the i386 referred to. I think the name Pentium was a "marketing thing".

---

### Post by Total Noob on 2010-07-09
Are the dual core and quad cores that come from Dell, Gateway, etc, 32's or 64's? 

How about Windows 7? Is if for 32 or 64 or both?

---

