---
title: "Hard Disc FAILING?!"
date: 2009-12-05
forum: General Help
---

### Post by dynamic.flare on 2009-12-05
Okay so I'm having lots of problems.  I just installed ubuntu 9.10 today.  It already says my hard disc is failing and has I think 52  bad sectors.... this is a brand freaking new dell laptop.  What the hell is going on??

more questions....

will post new thread.  Terminal not listening to me!

thanks :)

---

### Post by fluffman86 on 2009-12-05
Make a back up of your hard drive, then disable the message with System > Administration > Disk Utility > [Disk with Error] > More Information > "Don't Warn Me" checkbox near the middle of the page.

This is a known issue.  I've had this error for a couple of years now (when running the utility manually) and never had a problem.  You may want to keep an eye on this to make sure that the number of bad sectors isn't rising rapidly, and keep an ear out for any clicking from the HDD.

Remember! Even if your disk *isn't* failing *NOW*, it could at any time.  I always keep a current backup on another disk of another brand of another age, and also put a backup in a safe deposit box at the bank or at my mom's house or somewhere else offsite (in case of fire, theft, etc.).

---

### Post by em3raldxiii on 2009-12-05
The application that tells you about the bad sectors is just reporting information that is gathered by your hard drive's SMART reporting program.  Net result?  Your hard drive is failing already.  Yes, this happens.  Part of the reason is that many of the big box computer companies (like Dell, HP, gateway, etc) use "third party" and "OEM" manufacturers of hardware, and often that hardware is less than top quality.  Also, statistically speaking, hard drives are the hardware with the highest failure rate.

What should you do:  First off, don't panic.  It is likely your hard drive will be okay for a few days (and maybe longer).  So back up all your sensitive data (make use of ubuntu one!!  2GB of free storage in the "Cloud"!!  Great for this situation.  Second, you should replace your hard drive as soon as you can.  It is not likely that this is a false alarm; in my experience, if Ubuntu tells you your hard drive is dying, then it's probably dying.

If it's a desktop computer, you can get a new hard drive for $100 or less from many online retailers, or get Dell to replace it (you might get junk though).  I recommend the Western Digital "Green" tagged drives.  If it is a Laptop, you might do well to contact your laptop vendor and have them replace the drive.

Replacing a hard drive is easy easy easy easy.  So easy.  Just take care not to jab your computer parts with a screwdriver and you should be fine.

---

### Post by judge jankum on 2009-12-05
You're not suppose to jab everything with the screw driver? RATS!!!!

---

### Post by fluffman86 on 2009-12-05
> **em3raldxiii said:**
> The application that tells you about the bad sectors is just reporting information that is gathered by your hard drive's SMART reporting program.  Net result?  Your hard drive is failing already.
Um, no.  Going to have to disagree, sorry.

1. This is a *new* hard drive.  Odds are it's actually not failing...not this quickly.  

2. 52 sectors is *nothing!*  That's possible straight from the factory, and certainly after running Windows for any length of time.  In fact, I would wager that those 52 are just misreported and a [shred](http://en.wikipedia.org/wiki/Shred_%28Unix%29) of the drive would probably fix things...but why worry if the bad sectors aren't increasing?  

3. You said it yourself...SMART is reporting info from the drive manufacturer.  Now, if you sold cars, and someone asked if they should replace their car or take it to a mechanic, what would you tell them?  "Buy a new car, of course!"  I'm *not* saying that HDD manufacturers are doing this, but it is awfully coincidental.  :P

4. Again, per the OP, "this is a brand freaking new laptop" which means it's under warranty.  Suggesting that they replace the drive by buying one while their current one is under warranty is just silly.  *IF* the drive is failing (which it's probably not), then it can be returned and replaced, with the proper instructions from Dell and without risk of voiding any warranty.

edit:

5. Also, there's nothing wrong with OEM drives.  Maybe OEM RAM might be a little slower, or OEM drives might be a little cheaper, but their not going to fail while still "brand freaking new".  I've worked extensively with Dells at an all-dell university and our HD failure rate was really pretty low.  Out of some 1000+ machines that I worked on, I may have dealt with 3-5 bad (and I mean totally bad) drives per year.  And that was on 3-4 year old machines, on average.  

6. Even without all of that, this is still a known issue with Karmic.  In fact, the error will possibly even go away once the OP runs an upgrade.

---

### Post by em3raldxiii on 2009-12-05
> **judge jankum said:**
> You're not suppose to jab everything with the screw driver? RATS!!!!

It's funny you mention that LOL.  A few years ago, I was trying to undo the clip holding the heat sink on an Athlon XP processor, and it slipped (LOL, like that never happens), and I jabbed the board below one of the PCI card slots.  It seemed to be fine, and I couldn't see any physical damage, so I shrugged and fired it up.  No problem.

A couple of weeks later, the board died.  I looked at the board, and lo, there right where I musta jabbed the board, was a surprisingly large 'roasted electronics' scar.  I think I musta squished one of those wee little resistors or caused a wee arc between two circuits.  Anyway, lesson learned:  Don't do that. ;)

---

### Post by em3raldxiii on 2009-12-05
> **fluffman86 said:**
> Um, no.  Going to have to disagree, sorry.

Well, I look at it this way:  With number of drives that I have encountered where there are bad sectors and the drive eventually (fairly soon) does fail catastrophically, I have gotten to the point where I just replace the drive by default.  I begin to assume that early signs might indicate a deeper problem with the hardware (since that is what I do).  It's purely from personal experience.  You will note that I recommended he take his laptop to his vendor to have the drive replaced, and that he can have Dell replace it either way. :D  It's all about helpin' me fellow Ubuntu buddies.

Also, like I said before, make use of Ubuntu One!  It is your friend.

---

### Post by fluffman86 on 2009-12-05
> **em3raldxiii said:**
> a surprisingly large 'roasted electronics' scar

hahaha.  those are awesome.  Reminds me of the first time I took a computer apart completely and forgot to/couldn't (because of fat hands) put the heatsink back on.  Computer turned on fine, got to the BIOS, and then it died.  Apparently I let all of the magic smoke out...:popcorn:

---

### Post by em3raldxiii on 2009-12-05
> **fluffman86 said:**
> hahaha.  those are awesome.  Reminds me of the first time I took a computer apart completely and forgot to/couldn't (because of fat hands) put the heatsink back on.  Computer turned on fine, got to the BIOS, and then it died.  Apparently I let all of the magic smoke out...:popcorn:

Hehe, I love magic electronics smoke ... did you get the purplish kind, or the greenish kind?  hehe ;)

---

### Post by fluffman86 on 2009-12-05
I remember seeing a big, bright, blue spark, and then I think it was a bluish-purple smoke.  I didn't stick around long, though, thanks to the awful smell!  :P

---

### Post by em3raldxiii on 2009-12-05
Oh yeah, been there.  Bright sparks.  I've had a few power supplies go out on me like that, quite the blaze of glory.  One of them gave me this warning wail (I think it was the fan, but I never did find out).  The wail got louder, but lower-pitched, and then sparky display followed by the bluish smoke.  And to top it all off, the processor was also fried in the same stroke (It was one of those old Duron processors) - had the brown blisters under the processor.  Pure awesomeness right there.

Luckily, hard drives don't seem to be so spectacular when they go down, it's more like they lay down and give up.  Sometimes with Tourrettes.  Interestingly, the magnets from the inside of your hard drive are incredibly strong.  GREAT fun to play with, but also useful (put them on a piece of twine and use it for retrieving metallic tools from hard to reach places).

---

### Post by judge jankum on 2009-12-05
There's nothing like the "stank" of a computer blowing straight up to the ceiling just after a screw driver scob  LMAO!!!

---

### Post by egalvan on 2009-12-05
> **fluffman86 said:**
> Um, no.  Going to have to disagree, sorry.

1. This is a *new* hard drive.  Odds are it's actually not failing...not this quickly.

True, but it COULD be failing, which is why new parts generally have warranties.

> 
3. You said it yourself...SMART is reporting info from the drive manufacturer.  if you sold cars, and someone asked if they should replace their car or take it to a mechanic, what would you tell them?  "Buy a new car, of course!"  I'm *not* saying that HDD manufacturers are doing this, but it is awfully coincidental.  :P


Technically, SMART is reporting information that the drive itself is giving... the manufacturers do not "make it up" or "fudge it"
and SMART does not tell anyone to "buy a new drive" :)
it merely reports info that allows the user to determine (more or less) the health of the drive...
No coincidence, or conspiracy.

> 
5.  there's nothing wrong with OEM drives.  Maybe OEM RAM might be a little slower, or OEM drives might be a little cheaper, but their not going to fail while still "brand freaking new". 


Agreed, there is nothing wrong with OEM anything...
[COLOR="Red"]OEM[/COLOR] stands for [COLOR="Red"]O[/COLOR]riginal [COLOR="Red"]E[/COLOR]quipment [COLOR="Red"]M[/COLOR]anufacturer,
which is the company that [COLOR="Red"]M[/COLOR]anufactured the [COLOR="Red"]E[/COLOR]quipment that[COLOR="Red"] O[/COLOR]riginally came in your new machine.
Neither Dell, or HP or other computer makers make their own parts,
they spec them out and buy them from other companies, such as Western Digital, or Seagate, etc.
Also, the warranty is usually transferred to the assembler, such as Dell or HP, who can offer longer or more liberal warranties...
or shorter...

This is common in many other segments of manufacturing, such as automotive, appliances, electronics, etc.

It seems that many folk think that OEM stands for Cheaper Stuff...

---

### Post by dynamic.flare on 2009-12-05
okay so this computer is literally a week or 2 old.  

I don't get how it can be failing but it was hard enough waiting for the damn laptop to be shipped.  Would hate to have to send it back.

What are the chances I wait a few more months to see what happens and then if the bad sectors increase, I send it back before the warranty expires?

How would I have known this with windows?  I guess I wouldn't have?  

Anyway, I'm a she not a he.

Thanks for your help!

---

### Post by em3raldxiii on 2009-12-05
Well, very likely, the hard drive will be functional for several weeks, if not a lot longer; however, it's basically telling me that it's not trustworthy and you should definitely make sure that you back up any important documents to an online storage solution, or to a handy dandy memory thumb-drive.  Also, if you have downloaded and isntalled World of Warcraft (or any other big games like those that come with Steam) with all of it's incredibly huge amount of update and patch data, you might want to copy that entire directory to a thumb drive so you don't have to go through the pain of doing that after you replace the drive.

And regarding my offhand comment about "OEM" manufacturers, I should clarify.  There are reputable OEM manufacturers like Seagate and Western Digital, and then there are the less reputable ones and even 3rd and 4th party redistributors.  The net result, when someone gets a "Dell" drive, it will have been manufactured by someone else, and unless you do some homework, you may never know who the likely manufacturer actually was ... which means you could get a drive that I would feel less comfortable with.  Mind you, even manufacturers like Seagate have duds - their drives marked 7200.11 are a prime example.  And with those big box companies, you know that they are more concerned with their bottom line than anything else.  As long as a statistically large enough number of their drives (and other hardware) never come in for warranty work, they're happy.  :D

---

