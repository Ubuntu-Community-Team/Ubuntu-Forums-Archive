---
title: "ideas: intel atom with ssd hd or"
date: 2012-01-01
forum: General Help
---

### Post by markMDW on 2012-01-01
Hi, I'm seeking ideas for building the lowest cost GOOD computer possible.  Besides being inexpensive I'd like it to have agile performance, compactness, quietness and ease of assembly and setup.  I'm thinking of building a basic system with intel atom and 4GB RAM and using the advice in this tread to save data and/or the home directory to external and swappable memory storage:
[http://ubuntuforums.org/showthread.php?t=1785567](http://ubuntuforums.org/showthread.php?t=1785567)

   questions:
-  Could anyone explain why SSD is much faster and much costlier than USB memory?  Instead of a mechanical harddrive I want to use a small SSD-HD, perhaps 8 to 16GB and store the Home directory links to USB or SDHD flash.  Then i noticed the price for a bootable SSD-HD.  A 16GB is around $60.  Now for USB or SDHD Flash the same amount of memory is only $16.  I see a spec that says the SDHD is "class 4" which I understand to mean 4X normal CD ROM speed (so that would be the same memory speed as a 4X CD-ROM... That's SLOW.  Why is SSD bootable memory so much more costly than USB or SDHD memory for the same amount?  Also, I suppose that booting from SSD-HD would be much much faster than booting from USB.  Otherwise, I would like my low spec system to boot from USB rather than HD.

-  Would the latest Intel itx motherboard w/Atom run Unity in 2D mode or standard mode?  I'm familiar with Xubuntu and love it because of its simplicity and lack of distractions to getting things done.  I've never used Unity, but actually after researching it I am very impressed.  I think Canonical deserves kudos and accolades rather than scorn for attempting to create a new computer experience that offers the Linux yet community another real choice rather than just another Distribution but with a their own different wallpaper etc.

-  Can I skip the case w/power supply and just buy a very inexpensive power supply and wrap it all up in some nifty wrapping solution behind the monitor?  

-  Does anyone think I could get a GOOD computer experience running Puppy Linux or Bodhi Linux, from bootable USB, and skipping the SSD-HD?

Thanks for everyones ideas.. HAPPY NEW YEAR!   :KS

---

### Post by snowpine on 2012-01-01
Have you used an Intel Atom before? It is a very slow processor, comparable to a fast Pentium 3 or slow Pentium 4. In my experience, this is plenty for light-duty Xubuntu (web surfing etc) but Unity will drag unless you have a good graphics card.

If I was on a very tight budget, personally, I would find a used computer in the $0-100 price range on Craigslist, Freecycle, Goodwill, friends, relatives, co-workers, etc. that exceeds the Ubuntu Hardware Requrements described here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Another alternative is to find an inexpensive Atom netbook and add an external monitor, keyboard, and mouse. This will give you a slow "desktop" computer that is also portable if you need it. I do exactly this with my Asus EEE 900ha. :)

To answer another of your questions, fast SSD drives are expensive because they are fast. :) You will not get comparable performance from an SD card or USB device of any type.

---

### Post by Paqman on 2012-01-01
> **markMDW said:**
> -  Could anyone explain why SSD is much faster and much costlier than USB memory?


A proper SSD drive is both faster and more durable than the same size USB stick or HD card. A critical point is that an SSD will do wear-levelling to ensure the drive has a long lifespan. Large amounts of random writes like you'll get running an OS will wear a hole in flash memory pretty quickly unless it spreads the writes across the drive.

> 
I see a spec that says the SDHD is "class 4" which I understand to mean 4X normal CD ROM speed


Not quite. Class 4 SD cards have a write speed of 4MB/s. Which like you say is slooooooow.

> 
-  Would the latest Intel itx motherboard w/Atom run Unity in 2D mode or standard mode?  

Depends on the actual chipset. If it's one with a decent GPU then it would run full Unity, if it's only nasty Intel graphics then you'd be looking at Unity-2D.

> 
-  Can I skip the case w/power supply and just buy a very inexpensive power supply and wrap it all up in some nifty wrapping solution behind the monitor?  

Cases are largely cosmetic on small machines. Since you probably won't need any cooling other than the CPU fan you could put it in anything you liked as long as it was ventilated and insulated.

I would advise against trying to skimp on the power supply. It's one of the most important componants in the system. Most of the ones that come with cases are junk. If you're going to save on the case spend that money on a good PSU, it'll protect the investment you've made in the other componants.

---

### Post by markMDW on 2012-01-01
Thanks for the great advice!  A couple of years ago I used an Atom and it was slow running XP, which i understand is a tight os.  The newer ones such as the D525I would purchase has faster specs (of course) such as DDR3 memory,  plus great online reviews for internet surfing and running office type software.  I wasn't planning on heavy duty applications or playing DVD home theater movies on Big Screen TVs etc.   You tube in fullscreen might very well be its most intensive task.  

I've grown partial to the processor after reading so much marketing about it.  Now I'm getting the urge to build something 'brand new' and on a tight budget!  In the mean time i have refurbished a desktop circa 2001 and a laptop circa Vista era (was slow as molasses) both with Xubuntu 10.04 (the later 11.04 and 11.10 releases failed for some reason).  Lubuntu seemed slightly too generic for me.

---

### Post by snowpine on 2012-01-01
> **markMDW said:**
> You tube in fullscreen might very well be its most intensive task.

You'll definitely want a good video card for fullscreen flash video. Atom with integrated graphics can be a little painful for this task...

---

### Post by markMDW on 2012-01-01
Paqman, that answered my questions.  :D  BTW, I would be using just the basic Intel nasty graphics "Integrated Intel GMA3150 Graphics Controller"  How does that spec out?  I read that as 2D only.  

Regarding a potential homemade case.  Does it need to be metal to keep the little motherboard grounded, or could something plastic I conjure up work since the power supply would have a 3prong electrical connector (grounded)?   Thanks!

---

### Post by Paqman on 2012-01-01
> **markMDW said:**
> Paqman, that answered my questions.  :D  BTW, I would be using just the basic Intel nasty graphics "Integrated Intel GMA3150 Graphics Controller"  How does that spec out?  I read that as 2D only. 

I don't know anything about that chipset, but I would expect so, yes. 

> 
Regarding a potential homemade case.  Does it need to be metal to keep the little motherboard grounded, or could something plastic I conjure up work since the power supply would have a 3prong electrical connector (grounded)?   Thanks!

You want it to insulate, not ground the mobo. Normal cases are themselves grounded, and then that chassis is insulated from the mobo. Shorting a mobo to ground is a good way to conjure the expensive blue smoke of despair (or more likely it just won't power up).

A plastic box would work absolutely fine, as long as it provided adequate ventilation. You are correct that the mobo gets its ground through the power supply.

---

