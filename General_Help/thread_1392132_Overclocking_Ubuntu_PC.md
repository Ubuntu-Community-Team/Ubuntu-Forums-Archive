---
title: "Overclocking Ubuntu PC?"
date: 2010-01-27
forum: General Help
---

### Post by t0p on 2010-01-27
Could someone please explain to a clueless fool (me) how to go about overclocking my PC?  It's got a Pentium 4 processor, 1.7GHz... and it's running Ubuntu Hardy (if that's relevant).  Is there a program I can use to overclock my computer, or do I need to open up the case and do things to the motherboard?  Cheers.

---

### Post by t4thfavor on 2010-01-27
Newer intel chips are difficult to unlock, hence the reason for the XTreme editions which are unlocked.


What I mean is no you cannot overclock it without far too much trouble.

---

### Post by llawwehttam on 2010-01-27
You generally overclock using the BIOS. It is the most stable way of overclocking but be very careful. If you get any problems it could kill your computer.

Watch this: [http://www.youtube.com/watch?v=TeBk4j5E0dg](http://www.youtube.com/watch?v=TeBk4j5E0dg)
and the part 2 and 3

It will explain it very simply

---

### Post by pirateghost on 2010-01-27
> **t4thfavor said:**
> Newer intel chips are difficult to unlock, hence the reason for the XTreme editions which are unlocked.


What I mean is no you cannot overclock it without far too much trouble.


there is no reason to 'unlock' chips.  all overclocking 'should' be done in the BIOS, as the items that are handled for overclocking these days are all done by playing with FSB, Memory Ratios, and voltages on the motherboard.  the actual cpu just limits the top end.

it absolutely does not require an xtreme edition anything to overclock, those are a waste of money.  HOWEVER, do not expect any easy way of overclocking a prebuilt computer (dell, hp, sony, etc)

i have been overclocking for years, and it does not require any special software or windows.  memtest, superpi and temp monitoring (and a calculator for playing in BIOS) are pretty much all that is needed to thoroughly test your setup.

i even have an overclocked ESXi server.

---

### Post by cbeneke on 2010-01-27
Overclocking usually requires that you buy an enthusiast level motherboard.  It's usually a bunch of settings in the BIOS.  With a Core i7, there are so many variables you can tweak.  One thing you need to watch out for is temperature.  Usually the stock fans that come with a processor just don't do the trick.

---

### Post by warfacegod on 2010-01-27
Overclocking is not to be taken lightly. It is very easy to ruin hardware doing it. A more simple and safer solution would be to either buy a new CPU or a new computer entirely. If you decide to go through with this, be sure to do the overclocking in very small steps.

---

### Post by pirateghost on 2010-01-27
[http://www.ocforums.com](http://www.ocforums.com)

they have tons of guides on how to overclock and what to look for when doing so.  its easy to do, but its also easy to screw up.

---

### Post by t4thfavor on 2010-01-27
P4 Chips are locked meaning you cannot mess with the chip multiplier, making it more difficult to overclock RELIABLY. Modifying the FSB alone open up the door to many more problems. You could smoke RAM, parts of the MOBO, etc. Whhereas if you just change the CPU multiplier you just have to cool it better.

Hence the Intel Xtreme chips that have an unlocked (raise and lower) multiplier instead of a standard "only lowerable multiplier".

---

### Post by pirateghost on 2010-01-27
> **t4thfavor said:**
> P4 Chips are locked meaning you cannot mess with the chip multiplier, making it more difficult to overclock RELIABLY. Modifying the FSB alone open up the door to many more problems. You could smoke RAM, parts of the MOBO, etc. Whhereas if you just change the CPU multiplier you just have to cool it better.

Hence the Intel Xtreme chips that have an unlocked (raise and lower) multiplier instead of a standard "only lowerable multiplier".
LOL.  seriously...

i am not a noob in the overclocking world, i have been doing it for years on SEVERAL machines.

there are a lot of 'LOCKED' cpus.  you have to get a good balance of fsb/ram timings/ram speed/etc so that you dont overclock those beyond what the overall setup can handle.

this takes a lot of reading and understanding to get into.  telling someone to get an xtreme chip so they can overclock is like telling someone they have to buy a ferrari to get more speed, when a mustang will do them fine with some tweaks, modifications and comprehension of whats going on under the hood.

if you buy an xtreme chip, whats the point of overclocking?  you just spent $1000 bucks on a chip...

the philosophy behind overclocking lies in the fact that you can get those 'xtreme' speeds without having to fork over the dough.  this does however require the right components.  more than likely you wont 'smoke' anything, but you do open yourself up to risk if you think you can push 2.7v to a chip that cant handle anything over 1.8

most of the time, motherboards (even the lowend enthusiast level) have protection against permanent damage to any one part, they tend to just not boot up right if clocked too high (in which case you just use the BIOS reset jumper and go back to stock and try again).  the same cannot be said for software overclocking though.  with software overclocking, you are doing it in an OS that is already using those resources, and you can likely kill something by accidentally making a setting too high, and it tries to force that setting instantaneously.

i have my q9550 overclocked from 2.8ghz to 3.8ghz and its not 'an xtreme chip' and i am not running any risk of ruining anything with my setup because i know what i am doing.

i am not recommending that the OP just jump into it, but rather recommending that some actual research and reading be done on it before attempting the task. 

the whole point is that the OS is not responsible for any of this and instead of posting on an OS forum, post on an overclocking forum where experts on the subject matter can actually help out.

---

### Post by Ginsu543 on 2010-01-27
^^ +1. As you can see in my siggy, I have my Intel Core2Duo E6600 overclocked from its stock 2.4 GHz to 3.4 GHz. The processor is locked (you can't change its multiplier), so the only way to overclock it is to change the FSB speed the motherboard runs at. Tweaking the FSB is a higher risk/higher returns process since increasing the FSB not only overclocks the CPU but all the components on the motherboard (including RAM). So you do have to proceed with caution. As someone noted above, it is advantageous to have good "enthusiast" components that are overclocking-friendly, but any system can be overclocked as long as it is done with care. The extent to which you can overclock depends on the components you have, and even the same exact components will overclock differently.

As pirateghost recommended, you should go to overclocking forum sites and read up on how to overclock, ask questions, and get familiar with the process before proceding. I have overclocked every single computer I have ever owned (well, except the very first one, which was the only one I did not build on my own) and it has served me well. Case in point, it has extended the life of usefulness of my current rig well beyond the typical 3-5 year upgrade cycle for computers.

---

### Post by t0p on 2010-01-28
Thanks for all the replies. I'm going to go do some reading. I'll also check out the resources linked to by some of you. This is obviously a subject that needs serious investigation.

---

### Post by MooPi on 2010-01-28
If your just overclocking to get some extra speed out of old dog, work slowly and in small steps. Bump the speed up in small increments and test for stability afterwards. My suggestion would be prime95 tress testing. Prime halts operation on an error and gives you a good indication that the overclock is not stable and may harm the system. Good luck.

---

### Post by llawwehttam on 2010-01-28
Its always good to search for people who have overclocked using your processor and they may be able to tell you some stable overclock values.

---

