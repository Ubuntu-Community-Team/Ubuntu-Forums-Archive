---
title: "Is this the best solution for the wireless broadcom problems?"
date: 2010-01-10
forum: General Help
---

### Post by Biciclettapc on 2010-01-10
Working a lot on a friends computer with no real success getting his broadcom 4306 wireless adapter to work.  The guy isnt a real techie and I dont want to give him a computer back that requires him to constantly have to jump through hoops to get the wireless working on the laptop.  Its an older HP zv6000 that used to run Xp, slowly....  Ubu, Linux, is the best option IMO to give him a well running computer without the cost of a new system.

So, if I suggest something like this, or one I know is Ubu compatible is this the best option?  
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833162030](http://www.newegg.com/Product/Product.aspx?Item=N82E16833162030)

I realise this one may not be Ubu compatible but something along these lines?

Thanks!
Paul

---

### Post by QLee on 2010-01-10
You should be able to get the 4306 to work after loading the necessary proprietary firmware (that's why it isn't shipped with the operating system, it proprietary, not "free").

I have no idea about the hardware you cited, but you shouldn't need additional hardware if the 4306 card in the unit is functioning.

---

### Post by Biciclettapc on 2010-01-10
Qlee, wish it was that easy!  All restricted drivers are installed, several different variations of solutions have been tried with no luck.

If you got a solution let me know I am willing try it too!

Lots of people are having issues with getting broadcom wireless to work.

---

### Post by stomakmonkee on 2010-01-10
Have you tried using ndiswrapper at all?  With my Broadcom (previous to 9.10) that was all that would work.

---

### Post by stinkeye on 2010-01-10
Have you seen this thread.
[_**[COLOR="DarkRed"]The Definitive 9.10 Broadcom Solution Guide[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=1368699&highlight=definitive+broadcom")
Halfway down the first post it specifically mentions your card.

---

### Post by Biciclettapc on 2010-01-10
I've tried so much stuff, and re-installed os so many times I forgot what I've done!  Key in 4306 in a search and you can see the many options out there.

Odd thing is it will work sometimes when there is a hard wire plugged in, which defeats the purpose, but as soon as its disconnected from hard it wont work on restart.

I actually had it working the other day and gave him back the computer, but after a few days quit working.  So back to the drawing board.

I am soon to d/l 9.04 and try that version of Ubu and see if I can get it to work.....  Last resort, which may be the only resort is back to Windows on the computer.  Its just SLOW....  its a old computer with low memory (upgrading) and the guy doesnt have the money to buy a new system.  I thought I was helping him out, LOL, by sticking Ubu on.  He did say when Ubu was working it had brought him from dark to the light!

---

### Post by Biciclettapc on 2010-01-10
Stinkeye,  I dont think I have done that solution yet.  

I am willing to give it a try!  It will be a few hours before I am home and can give it a shot, but I will.

---

### Post by QLee on 2010-01-10
[QUOTE=Biciclettapc]Qlee, wish it was that easy!  All restricted drivers are installed, several different variations of solutions have been tried with no luck.

If you got a solution let me know I am willing try it too![/QUOTE]

Well, my Broadcom 4306 works fine after I loaded the necessary firmware. It isn't possible to guess why it might not have worked for you or if you made some error. (mine is a rev 03)

You're sure the card itself is functioning OK, not intermittently? You wrote it worked then stopped, could it have stopped working after a kernel update, I seem to remember seeing a thread about that somewhere?

[QUOTE=Biciclettapc]Lots of people are having issues with getting broadcom wireless to work.[/QUOTE]

Lots of people are having troubles getting Ubuntu to "work" too, that doesn't mean there is anything inherently wrong with the operating system or that their problems aren't user created in many cases due to lack of understanding.

[QUOTE=Biciclettapc]Odd thing is it will work sometimes when there is a hard wire plugged in, which defeats the purpose, but as soon as its disconnected from hard it wont work on restart.[/QUOTE]

Don't be confused, the "hardwire" is using the ethernet card not the wireless card. They are two different things.

If,as you wrote, it's a low resources computer, you may get faster usage and better results with a lighter operating system, Ubuntu needs a decent computer to give the best user experience.

---

### Post by mfaust731 on 2010-01-10
Hey guys,
Ive been trying to help Biciclettapc via phone and email.
One important piece of the puzzle here is that he CAN see networks throught Network Manager, he just can not CONNECT to them.
He is running a 802.11 G network with no security.
It isnt a hw issue, because it was working fine the 1st go around, then the system files got hosed - I suspect it wasnt shut donw cleanly.

I have gotten many of the broadcoms working in the past, and I "think"
he has the driver set up right since he can see the network - But this one is beyond me, what else would not allow it to connect the network it finds.

Now that I think back, It seems I have had to manually set up a network in the past to get it working - but I havent had to do that in ages

Thanks for the help

---

### Post by QLee on 2010-01-10
[QUOTE=mfaust731]Hey guys,
Ive been trying to help Biciclettapc via phone and email.
One important piece of the puzzle here is that he CAN see networks throught Network Manager, he just can not CONNECT to them.
He is running a 802.11 G network with no security.[/QUOTE]

Well, we can only work with the data presented, we have no idea what was done or how it was done in private. That is the good thing about forums, peer review of all advice and results and many eyes to check our work.

[QUOTE=mfaust731]It isnt a hw issue, because it was working fine the 1st go around, then the system files got hosed - I suspect it wasnt shut donw cleanly.[/QUOTE]

Well, not shutting down cleanly doesn't usually "hose" system files. So, I can't justify ruling out a possible hardware problem.

[QUOTE=mfaust731]I have gotten many of the broadcoms working in the past, and I "think"
he has the driver set up right since he can see the network - But this one is beyond me, what else would not allow it to connect the network it finds.

Now that I think back, It seems I have had to manually set up a network in the past to get it working - but I havent had to do that in ages

Thanks for the help[/QUOTE]

OK, you're comfortable and competent doing it manually, when you are next on the phone to him try uninstalling (purge) network manager to get it out of the way and configure the setup manually which should give you the chance to see more info in the terminal as you are working. After you've got it working re-install network manager to give your client (or friend) automagic connection. 

Are there lots of nets shown when you do an iwlist scan, are they using the same channels to broadcast, is one, or more, of them higher power than his? Just some things to consider.

---

### Post by mfaust731 on 2010-01-10
QLee, 
Thanks for the input, I was just trying to clarify the issue with what I know of it - before we realized we needed help from you guys.
Im rusty on these steps, hadnt had to do them in while.
I'll keep all further steps taken here, any corrections are welcomed;)

Biciclettapc,

Open up a term, and run this.
Please post the result

sudo iwlist scan

---

### Post by QLee on 2010-01-10
OK, I see you chose to check for congestion first. I have had intermittent trouble connecting, and drop offs at a site with congestion on a single same channel, at that time the signal levels for the gateway I wanted to connect to seemed to be swamped out by stronger signals at times from nearby gateways which varied in strength over time but I've only seen this in one location and so it isn't definitive or necessarily common. Just one thing to consider.

I'd also check the edit of the connections that network manager already knows about from previously to make sure it isn't trying with some incorrect option. But, you've probably already checked that.

I'm leaving now but there are lots of knowledgeable people on the forum to help you. That link stinkeye posted looks like it could help.

---

### Post by Biciclettapc on 2010-01-10
Well after a long afternoon working with Mfaust731 over gmail chat we have struck out.

It must be the 4306 rev 03 card, computer, or alignment of the stars, but I have to cut my loses and put Xp back on the computer for this guy.

I STILL think Ubu is the best route!  BUT, not with the wireless broadcom.  Which takes me back to my original post on this thread.  Is a usb wireless adapter that WORKS with 9.10 an option to present to this guy?

Thanks for everyone help
Paul

---

### Post by raysfan81 on 2010-01-10
I have a hp dv 6000 laptop and I never could get the wireless to work for some reason.  Tried almost everything and it still wouldn't work.  I just switched back to 9.04 and everything works great again.  You might just want to try an older distro.

---

### Post by Biciclettapc on 2010-01-10
I am d/l the older distro right now.

Did you have ANY issues with getting it to work?

This might be the best option??????

---

### Post by stomakmonkee on 2010-01-10
> **raysfan81 said:**
> I have a hp dv 6000 laptop and I never could get the wireless to work for some reason.  Tried almost everything and it still wouldn't work.  I just switched back to 9.04 and everything works great again.  You might just want to try an older distro.

Weird.  I'm using 64bit 9.10 with an HP dv6604nr and it worked as soon as I enabled the restricted drivers.

---

### Post by Biciclettapc on 2010-01-10
The dv i bet is a higher level of HP laptop.  Not knocking this laptop but I know it was close to the bottom of the HP food chain when it was released.

---

### Post by mfaust731 on 2010-01-10
I cant figure it out.
Ndiswrapper wouldnt work, only way we can get the interface up is using the b43 driver in restricted drivers and then using fwcutter to get the firmware.
When we get the interface up, It can see the networks but will not connect.
the is only one other network listed in out scan but I dont see a conflict.
I have saw numerous posts regarding "this" chipset needs the B43Legacy driver, (or it will not connect) but it should be installed with the regular B43 driver. 
Any gurus have any other input?

---

