---
title: "soft lockup - CPU#0 stuck for 61s"
date: 2010-04-30
forum: General Help
---

### Post by Angelic on 2010-04-30
I recently installed 10.4 on my laptop and I love it, so I wanted to install it on my desktop. It's a somewhat older computer, AMD3000+ nForce 2, 1.5 gigs of Ram and a Radeon x1650. Whenever I try to start the Live CD I get the error soft lockup - CPU#0 stuck for 61s and it doesn't continue. Anyone know what could cause this?

---

### Post by carbonrobin on 2010-05-01
I also have this problem on an older desktop.  AMD Athlong XP 1800+ 1GB RAM ATI Radeon 9550  Currently dual boot Ubuntu 9.04 and Windows XP Pro SP3.

---

### Post by tgalati4 on 2010-05-01
First, clean out the machine and reseat the RAM.  Run memtest for 30 complete cycles.  This will take overnight.  If you pass with no errors, then we can start looking at other things.

Also, reseat the power connectors to the motherboard and reseat all ribbon cables and any other cards in the system.

---

### Post by greg_stager on 2010-05-02
I also had this issue.

My solution to this was to install 9.10 and then run the upgrade from within the program.

I know it is a bit of a work around but the 9.10 install CD worked where the 10.04 didn't. I suppose it could have been a problem with the disk I created but I did not look at that yet. I will try it on a different system when I get a chance and replace it if necessary.

Hope this was a help to someone.

Stags

---

### Post by Havokdan on 2010-05-02
I am with this problem, do not start the live cd, but when I press F6 and mark the option "nodemoset," the live cd starts, but when I do I install the screen is black and so I tried various solutions here, but as not had success yet, I'll wait for version 10.10 to try again, for the record is the first time I have problems installing ubuntu, always tried every version that was released since 7:04 with no problem, I was waiting for this release to effect a full exchange of windows xp to ubuntu. I hope I have better luck next version.

* I can read English, but what I write here is with the help of google translator.

---

### Post by carbonrobin on 2010-05-03
> **tgalati4 said:**
> First, clean out the machine and reseat the RAM.  Run memtest for 30 complete cycles.  This will take overnight.  If you pass with no errors, then we can start looking at other things.

Also, reseat the power connectors to the motherboard and reseat all ribbon cables and any other cards in the system.

I'll try that tonight. I do have a question about this, why would Ubuntu 9.04 and previous Live CDs work?

---

### Post by tgalati4 on 2010-05-03
It could be related to the PAE kernel in Lucid.  PAE--Physical Address Extension allows your 32-bit distro to see more than 4 GB.  It affects how RAM is addressed.  It's possible that your machine's CPU can't handle PAE--causing a lockup.

I don't know how to turn PAE off in Lucid.  The older, Live CD's use the normal kernel, which presumably works with your hardware.

The cleanout procedure is just to give you something to do until I can come up with a more creative solution.

#-o

---

### Post by MyotisSI on 2010-05-05
I have the same problem, I've installed 10.04. with alternate CD, I normally worked in ubuntu, but after restart I got a black screen and after a sea of code the line:
soft lockup - CPU#0 stuck for 61s!
:(
I think I'll revert to 9.10.


[COLOR=Red]**Update: 7. may 2010**[/COLOR]
I installed 9.10 and then upgraded via network to 10.04.
The install went smooth, but after the restart, there was again [B]soft lockup - CPU#0 stuck for ... :(

[/B]I reinstalled  9.10. For now that is the only solution I found.

---

### Post by WolfGero on 2010-05-11
I think I may have had the same problem:    

```
BUG: soft lockup - CPU#0 stuck for 61s! [plymouthd:401]

```I've got no solution but a workaround, adding ```
nomodeset
``` to the kernel parameters.  

To temporarily add a kernel parameter:

[LIST]
[*]press '***Esc***/Escape' for selecting a kernel at early boot time
[*]select your kernel and press ***e***
[*]add  *nomodeset* to the line and press enter, then ***b***
[/LIST]
 [LEFT]  Even using ```
radeon.modeset=0
``` is enough for me to get rid of the hanging boot.   Hope this helps some other people, too, since I only registered with ubuntu forums to leave this comment. :)    
Wolf  
---
(VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE])[/LEFT]

---

### Post by gary987 on 2010-05-28
I don't think is has anything to do with 4G+ memory, or to do with bad memory. 

My computer just started doing the bug...on Linux Mint as well. It wasn't there a couple of days after the install, but now it is.


Is everyone running an ATI card on a nforce2 board?

I just pulled my radeon 8500 out and tryed running the onboard Nvidia gforce and so far the bug hasn't come up again.

---

### Post by g3b on 2010-07-26
I've also had the same issue am using Athlon xp3200 cpu 1 gig ram & ati agp 3650 video card.  I was able to do a Wubi install with 9.10 ubuntu without issue, however the computer locks up on the reboot after initial install of 10.04 & requires a hard boot to get to the boot screen again.  Will try the Wubi 10.10 installer.

g3b

---

### Post by anthony luppino on 2010-11-14
> **gary987 said:**
> I don't think is has anything to do with 4G+ memory, or to do with bad memory. 

My computer just started doing the bug...on Linux Mint as well. It wasn't there a couple of days after the install, but now it is.


Is everyone running an ATI card on a nforce2 board?

I just pulled my radeon 8500 out and tryed running the onboard Nvidia gforce and so far the bug hasn't come up again.


I also the same error with an ATI Radeon video card installed on a Asus A7N266-VM board. I have removed the video card, and by using the on board graphics card the error has disappeared

---

