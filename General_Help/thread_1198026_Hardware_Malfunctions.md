---
title: "Hardware Malfunctions"
date: 2009-06-26
forum: General Help
---

### Post by Arukas on 2009-06-26
In short, I believe I have a hardware problem, and I have no clue what it could be.  Anyone know any tool in Ubuntu that can track a problem down?  

The above was the short story for the people that likes the point.  Listed below is more of the story.  

Here's the deal.  I play WoW in windows, and it started magically crashing.  I talk to a tech and they was blaming my computer.  So I decided to see if WoW would run in Ubuntu (8.04) under wine. I've been meaning to try it.  But WINE produce the same instant reset problem that I had in windows. 

So now, I believe I have a hardware problem, and I don't know what it could be?

---

### Post by RedSingularity on 2009-06-26
If you are getting the same problem in both Operating systems it has to be a hardware problem.  Linux is **Definitely** not windows and it should work in one if not the other.  But you say you are having a problem with both so................i go with hardware.

---

### Post by Arukas on 2009-06-26
I forgot to mention something.  The reason, I didn't think it was my computer, was that Warcraft was the only program that caused this error.  Now, 

I agree with you that Linux is better than Windows, and I am willing to belive its a hardware problem.

The question is, how do I find this problem?

---

### Post by philcamlin on 2009-06-26
clean out your pc because aparently gaming heats up your c and if its dusty itll overheat and crash :popcorn:

---

### Post by Arukas on 2009-06-26
I don't think it overheating is the problem.  I'll do it anyways.


However, this is on a frest start up before the games gets going, and heats up.  Besides, my computer can run games that acutally put stress on the machine.  Also, the high fans aren't kicking into high gear, like they do sometimes.  And I have never had a heating problem before.

---

### Post by Steelmourne on 2009-06-26
You could try patching WoW, and it might be a driver issue. Try upgrading to the newest drivers, both sound and video in Win and video in Ubuntu.

---

### Post by tgalati4 on 2009-06-26
You didn't tell us your hardware so we can only guess.

If embedded Intel, then the ethernet and sound are bundled on the same chip.  This can cause problems when playing a network game.  Local games only use the sound chip so they won't push the chip over the heat trip.

Look in /var/log and report errors.

Also:

dmesg | tail

when the machine is acting strange just before a crash.

Run memtest from a Live CD.  Run for 30 complete cycles.  This will take overnight.  Bad ram can cause headaches.  Clean and reseat ram chips before running.

---

### Post by Arukas on 2009-06-27
How do you clean and reset the ram before running the memtest?


Also, is there a way that ubuntu will list what my system has, so it will make it easier to post the information in a usable reader format?

---

### Post by tgalati4 on 2009-06-27
If it's a desktop, you remove the case and push down the clips holding the RAM chips in place.  Take them out and blow out the dust with compressed air.

If it's a laptop, remove the cover on the bottom and use a small screwdriver to push the metal clips back that hold the RAM in.

For hardware info, do the following in a terminal:

sudo apt-get install hwinfo

hwinfo

Cut and paste

---

### Post by synapsys on 2009-06-27
I think tgalati is on the right track. I recently had a problem with firefox randomly crashing for no apparent reason. I thought it was a firefox problem because my computer would run other programs fine for hours on end. Finally, I ran a memtest which INSTANTLY found errors. Got some new gskill and all is well.

---

### Post by DeMus on 2009-06-27
> **Arukas said:**
> In short, I believe I have a hardware problem, and I have no clue what it could be.  Anyone know any tool in Ubuntu that can track a problem down?  

The above was the short story for the people that likes the point.  Listed below is more of the story.  

Here's the deal.  I play WoW in windows, and it started magically crashing.  I talk to a tech and they was blaming my computer.  So I decided to see if WoW would run in Ubuntu (8.04) under wine. I've been meaning to try it.  But WINE produce the same instant reset problem that I had in windows. 

So now, I believe I have a hardware problem, and I don't know what it could be?

If it's only with this game then it is not a hardware issue. If all other software runs fine, including other games which stress the cpu, then your hardware is fine.
Somehow this game you have is not good, try to get another copy. I presume you ran this version both in Windows and in Linux through Wine? Get another copy and see what that does.

---

### Post by Arukas on 2009-06-27
I have a slight update.

The problem with my computer reset itselfs seems to be getting worse now.  It seem to reset itself when I first started doing the mem test.  Its running now fine, but the computer rested.

Does this mean anything besides I got a hardware problem?  Does it point to anything in particular?  I am going to leave the MEM test on, to see what it comes up with tomorrow morning.

---

### Post by Arukas on 2009-06-27
I been running my memory test, the one that on the ubuntu live cd, and there's been no errors mem errors for 9 hours.

I have a 
biostar mother board, ta770 a2+
4 gigs of ram
Athlon 64 X2 3100 MHz
Nvida 8800 GTX Video Card


I build this computer earlier this year and haven't had a problem with it until a couple of weeks ago.  


I have reinstalled the game, and I've run checks on the image.  I believe the instance reset is hardware problem.  

Either way, Hardware or software, I don't know how to track the problem down.

---

### Post by tgalati4 on 2009-06-27
I would now suspect the power supply.  The Nvidia draws a lot of power (perhaps 120 watts).  Combined with 4 GB of RAM and your Athlon 64 and how many disk drives?

You can monitor voltage using lm-sensors or plug a voltmeter into a spare power connector.  Any drops from 5V or 12V during boot could indicate that the power supply is ready to release the magic smoke.

It's possible that the motherboard has developed a problem.  The surface mount interface chips heat up and warp, causing cracks in the solder.  It doesn't take much contact resistance to mess up digital signals at 3 GHz.  These are hard to diagnose.  You can declock--run at half speed for a while and see if that improves reliability.

Place your finger on any exposed chips and if they are hotter than you can stand then the motherboard is ready to release the magic smoke.

---

### Post by Arukas on 2009-06-27
I have one cdroom and two hard drives.  


My first thoughts was it was the power supply, but I couldn't get the power supply to act up when I played my 3d games which draws a lot of power.  

Okay, I understand how it could be the mother board and/or the powersupply.  

My question if the CPU was going bad, would it be more evident?

---

### Post by tgalati4 on 2009-06-28
How fresh is the heat sink paste on the CPU?

Are any of the motherboard support chips getting hot?

CPU's rarely go bad, unless you massively overclock.  Power supplies frequenty go bad due to cheap capacitors and mosfets.

---

### Post by Arukas on 2009-06-28
This computer is under a 6 months old.  when I opened it up, all looked very well.  Barely any dust.

Is there a stress test program, I can run to see if I can make my computer fail?  I've ran a memory test for 36 hours, and that didn't come up with any problems.

---

### Post by Tipped OuT on 2009-06-28
Are you up to date with your BIOS? Has your computer been under a lot of stress (keeping it on for a long time, playing resource extensive games or not good ventilation for your CPU) ?

---

### Post by Arukas on 2009-06-28
My BIOS are good, and the problem is just only resent.  No, my computer has not been under a lot of stress.  I been just surfing the web and playing world of warcraft.  That's hardly stressing the system.  

With the exception of this one problem, my computer works perfectly.


edit

My ventilation is good. I try to make sure my computer don't over heat.  I have had that issue before with other computers.

---

### Post by tgalati4 on 2009-06-29
Try declocking.  If you get several weeks of uptime then start ramping up to normal speed.  It's possible that your 3.1 Ghz processor only runs reliably at 2.8 GHz.  

There are several programs that will stress a cpu.

Try tux racer with all the high settings.  

openssl speed

search for superpi

---

