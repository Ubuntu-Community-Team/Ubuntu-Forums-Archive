---
title: "Installed Ubuntu, now I can't boot Windows 7"
date: 2010-03-12
forum: General Help
---

### Post by DieNacht on 2010-03-12
Hi, I just signed up and so I don't know if this is the place for this. Excuse me if it isn't.

I just installed Ubuntu (because of my love for Open Source). Took me a while because I'm not versed in computers. 

The problem is that now I can't boot Windows 7. I followed the guide that Lifehacker gives to dual boot Ubuntu and Win7, but i think I must have messed up somewhere along the way. 

This is what my Gparted looks like:

[http://tinypic.com/r/2hphi1g/5](http://tinypic.com/r/2hphi1g/5)

/sda1 is where all the stuff that I had in Windows 7 is (it is still there). /sda2 is where the Recovery things is (that is what is appearing when I boot my PC and tells me to choose between Ubuntu and Windows Vista (loader). Not sure why it says Vista as oppose to 7). /sda3 and 4 are for Linux (and swap memory. Whatever that is). 

I already tried to just hit the Vista Loader but when I do, it just sends me to this "recovery center" thing. I can't do anything pass it (it tells me that I can restore to a previous point, but there are no points). 

I really like Ubuntu and the Open Source community and ideas, but I don't want to be forced into it (I still want to have Windows for several reasons. Though Wine is pretty cool). 

Does anyone know where I messed up and if it is fixable?

Thanks.

EDIT: SOLVED. 

Thanks MichaelH for the solution. For anyone looking the solution, the solution is this command:

sudo update-grub

Thanks again guys.

---

### Post by Tikkyca on 2010-03-12
i think you need to erase whole hard drive and install windows 7 agin.I would recommend you to use just ubuntu because it is great for everything AND for gaming,but pc's aren't for gaming that much if you like gaming buy a ps3 or xbox 360.

---

### Post by howefield on 2010-03-12
> **Tikkyca said:**
> i think you need to erase whole hard drive and install windows 7 agin.

Strange advice.

Reinstalling Windows should surely be the last resort, not the first.

@DieNacht, which version of grub are you using ?

---

### Post by DieNacht on 2010-03-12
> **Tikkyca said:**
> i think you need to erase whole hard drive and install windows 7 agin.I would recommend you to use just ubuntu because it is great for everything AND for gaming,but pc's aren't for gaming that much if you like gaming buy a ps3 or xbox 360.

That is a strange advice indeed. Also, PC's are the best gaming systems. In PCs you get to use a lot of indie games. In PS3 and Xbox, you are bond to what big publishers want (which is just money). 

> **howefield said:**
> Strange advice.

Reinstalling Windows should surely be the last resort, not the first.

@DieNacht, which version of grub are you using ?

I don't remember. I do remember that is was beta (it was 0. something).

I'll reboot and see.

---

### Post by Elfy on 2010-03-12
> **Tikkyca said:**
> i think you need to erase whole hard drive and install windows 7 agin.I would recommend you to use just ubuntu because it is great for everything AND for gaming,but pc's aren't for gaming that much if you like gaming buy a ps3 or xbox 360.

I would disagree with this.

The OP obviously needs some help with grub, not deleting OS's - that should be the last resort.

---

### Post by MichealH on 2010-03-12
> **forestpiskie said:**
> I would disagree with this.

The OP obviously needs some help with grub, not deleting OS's - that should be the last resort.

Thankyou I would point out that Reinstalling is my LAST resort because i have to backup ;) Anyway try ```
sudo update-grub
``` in a terminal and It may find windows...

It looks like you have a windows partition so you Obviously havn't wiped windows. Been there done that :(

---

### Post by Mark Phelps on 2010-03-12
If the update-grub fails to generate an entry for Win7 (will probably say something like Vista/Win7 loader on sdax), there's the possibility that the boot loader files are damaged.  In that case, you would have to restore them.

To do that, you would have to boot from a Win7 Repair CD and run Startup Repair a few times to get Win7 boot back.

Your failing to mention that CD leads me to believe that you failed to make such a CD when you were using Win7.

Unless you have a Win7 Installation DVD, which I doubt, go to the NeoSmart Technology forums, download the appropriate Win7 (32-bit or 64-bit) Repair CD image, burn that to CD.

You can use that to repair your Win7 boot.

---

### Post by MichealH on 2010-03-12
> **Mark Phelps said:**
> If the update-grub fails to generate an entry for Win7 (will probably say something like Vista/Win7 loader on sdax), there's the possibility that the boot loader files are damaged.  In that case, you would have to restore them.

To do that, you would have to boot from a Win7 Repair CD and run Startup Repair a few times to get Win7 boot back.

Your failing to mention that CD leads me to believe that you failed to make such a CD when you were using Win7.

Unless you have a Win7 Installation DVD, which I doubt, go to the NeoSmart Technology forums, download the appropriate Win7 (32-bit or 64-bit) Repair CD image, burn that to CD.

You can use that to repair your Win7 boot.

Or probably configure your grub.conf?

---

### Post by DieNacht on 2010-03-12
Ok, this is what my grub looks like:

[IMG]http://lh6.ggpht.com/_rWwkgX9-7Sw/S5qxjTbm4CI/AAAAAAAADGY/Gpmji2SWyrQ/s640/2010-03-12%2016.20.32.jpg[/IMG]

The highlighted one says what the second one says but without the "Recovery mode" thing in it (it is the normal boot. But you probably know that :)).

I'll try the update command.

---

### Post by Tikkyca on 2010-03-12
If someone is asking agin pc's are not maded to run just games like some people think,why you need to have strong pc to play new games?Because people less watch specs,then some other things,and they create a game that pc's cant handle.Do you see lag on consoles?No!Because they are for gaming,every game that is making has good performance for ps3 specs,also ps3 doesn't have system with THAT much processes in background,so you can play smooth without laggs.

---

### Post by MichealH on 2010-03-12
> **Tikkyca said:**
> If someone is asking agin pc's are not maded to run just games like some people think,why you need to have strong pc to play new games?Because people less watch specs,then some other things,and they create a game that pc's cant handle.Do you see lag on consoles?No!Because they are for gaming,every game that is making has good performance for ps3 specs,also ps3 doesn't have system with THAT much processes in background,so you can play smooth without laggs.

But we are not talking games here were talking GRUB I run Windows too for all my Schoolwork I can always just depend on Ubuntu.

---

### Post by Tikkyca on 2010-03-12
> **DieNacht said:**
> That is a strange advice indeed. Also, PC's are the best gaming systems. In PCs you get to use a lot of indie games. In PS3 and Xbox, you are bond to what big publishers want (which is just money). 



I don't remember. I do remember that is was beta (it was 0. something).

I'll reboot and see.

If someone is asking agin pc's are not maded to run just games like some people think,why you need to have strong pc to play new games?Because people less watch specs,then some other things,and they create a game that pc's cant handle.Do you see lag on consoles?No!Because they are for gaming,every game that is making has good performance for ps3 specs,also ps3 doesn't have system with THAT much processes in background,so you can play smooth without laggs.

---

### Post by MichealH on 2010-03-12
> **DieNacht said:**
> Ok, this is what my grub looks like:

[IMG]http://lh6.ggpht.com/_rWwkgX9-7Sw/S5qxjTbm4CI/AAAAAAAADGY/Gpmji2SWyrQ/s640/2010-03-12%2016.20.32.jpg[/IMG]

The highlighted one says what the second one says but without the "Recovery mode" thing in it (it is the normal boot. But you probably know that :)).

I'll try the update command.

Also, Are you sure you're running the RC or RTM? If you are running the RC it would come up as Win Vista Loader Like mine did

---

### Post by Tikkyca on 2010-03-12
> **MichealH said:**
> But we are not talking games here were talking GRUB I run Windows too for all my Schoolwork I can always just depend on Ubuntu.

Sry,will not happen agin,searching for a way to help...

---

### Post by howefield on 2010-03-12
> **Tikkyca said:**
> If someone is asking agin pc's are not maded to run just games like some people think,why you need to have strong pc to play new games?Because people less watch specs,then some other things,and they create a game that pc's cant handle.Do you see lag on consoles?No!Because they are for gaming,every game that is making has good performance for ps3 specs,also ps3 doesn't have system with THAT much processes in background,so you can play smooth without laggs.

Keep this for another thread, it has nothing to do with the question posed by the OP.

---

### Post by MichealH on 2010-03-12
> **Tikkyca said:**
> Sry,will not happen agin,searching for a way to help...

Probably sensible for the Cafe or Something where you can go offtopic :D

---

### Post by DieNacht on 2010-03-12
> **MichealH said:**
> Thankyou I would point out that Reinstalling is my LAST resort because i have to backup ;) Anyway try ```
sudo update-grub
``` in a terminal and It may find windows...

It looks like you have a windows partition so you Obviously havn't wiped windows. Been there done that :(

It worked!!!!! I just ran that command and the sda1 appeared. I'm typing this from Win7!

Thanks dude. You Rock! 

I'm going to keep using Ubuntu for a while and see how I like it (so far I like it, but I hate the fact that you have to put in a password for EVERYTHING. But I'm sure there's a way around that). 

Again, thanks. Thank you all.

---

### Post by MichealH on 2010-03-12
> **DieNacht said:**
> It worked!!!!! I just ran that command and the sda1 appeared. I'm typing this from Win7!

Thanks dude. You Rock! 

I'm going to keep using Ubuntu for a while and see how I like it (so far I like it, but I hate the fact that you have to put in a password for EVERYTHING. But I'm sure there's a way around that). 

Again, thanks. Thank you all.

Aww, Shucks! I have all the dualboot knowledge Because I do it and I know everything about it off the top of my head! If you would like your GRUB more beautiful see my sig! Again, Youre welcome!

---

### Post by Fuzzyducky on 2011-03-07
Hi Guys 


I have the same problem except I have windows on a separate HD so sda ubuntu and win7 sdb. when I boot up it just goes straight into Ubuntu, i would like a choice maybe with a button or make windows default as my mythtv project has failed. 

I have installed Ubuntu twice to try and fix it but no dice. Oh i must mention it started as Mythbuntu install as well, but i have added bits and pieces that its getting pretty close to full blown Ubuntu desktop.  

thanks in advance

Fuzz

---

### Post by Mark Phelps on 2011-03-07
> **Fuzzyducky said:**
> Hi Guys 


I have the same problem except I have windows on a separate HD  ...

Then you don't have the same problem, do you.

Please don't resurrect a post nearly a year old for a different problem.  Please start your own thread.

---

