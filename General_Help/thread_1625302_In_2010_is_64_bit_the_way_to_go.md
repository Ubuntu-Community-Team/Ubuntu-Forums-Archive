---
title: "In 2010 is 64 bit the way to go?"
date: 2010-11-18
forum: General Help
---

### Post by Todd S. on 2010-11-18
Most of my Googling of 64 bit vs 32 bit Ubuntu hasn't turned up much that isn't 2+ years old.  Is this an indicator that 64 bit is the preferable OS to install now?  Are the kinks worked out?

Also, what are the odds of getting Ubuntu (or more specifically Kubuntu) to run on this hardware setup: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834146853](http://www.newegg.com/Product/Product.aspx?Item=N82E16834146853)

Or perhaps I should say what are the odds of getting that hardware setup and the OS to play nicely?  I understand that ATI cards can cause problems at times, but I wonder if this isn't old information as well.

Any insight is appreciated.  I'm leaning towards the laptop that I linked as a dual-boot Win7/Kubuntu rig (with the Win partition existing primarily to play Civ V).  I have a Macbook Pro that I'm using now but it's rather old (2,2) and I don't know that installing Ubuntu/Kubuntu would go very well on it.

---

### Post by amauk on 2010-11-18
Definitely go 64 bit

There's one or two issues 64 bit, when it comes to proprietary software that is 32 bit only
(eg. Flash - although there is a 64bit beta flash library, so even that's going away)

Linux will run on pretty much any hardware, so not an issue

Not too familiar with AMD/ATI graphics cards
The open drivers should be no problem, but they may not offer 3D acceleration

I believe the issues are with the older cards when used with the ATI proprietary driver
Older cards (again, I believe) are neglected by AMD, in favour of providing support for their newer cards

---

### Post by leon_chame on 2010-11-18
I feel different as I have lots of issues with 64 bit...mostly due from bad/buggy software.

If you are simply going to 64 to get more memory, you can actually get the extra memory in 32 bit with PAE..and in my opinion probably the better option if all you are doing is going 64bit for the extra mem.

---

### Post by amauk on 2010-11-18
@leon_chame: OT, but I'd be interested to know what issues you've had?

---

### Post by Todd S. on 2010-11-18
Thank you.  It does seem like I'll be able to do what I want then.  

I've been looking for an excuse to get back into the *NIX world.  It's been about 10 years since I've done much.  Went from Suse to Slackware then abandoned Linux for FreeBSD and finally ended up with Mac OS X.  I've been getting tired of Apple's proprietary nonsense though, so I felt it was time to return to my roots.  I'm approaching it as a complete neophyte though - it's been a long time and I don't want to assume I know more than I really do.

I'm not really looking at it from a memory aspect - just that nearly every architecture you're going to get new is 64 bit.  The laptop in question comes preinstalled with Win 64 bit, so it can't be too bleeding edge at this point.

I can always play with it and revert to 32 (or install some 32 bit conversion tools) if need be.

---

### Post by dcstar on 2010-11-19
Are people **still** using 32-bit?!?

Seriously, I have been using 64-bit Ubuntu for about 3 years now and the only annoying issue is Adobe not having a released 64-bit Flash plugin at the moment (but they keep promising.....)

---

### Post by Bitrate on 2010-11-19
The choice of going 64-bit or not depends mainly on what applications you intend to run and the specs of your hardware.

I chose to go 64-bit for Linux because it's mature and well supported (mostly, baring some codec issues). If you work with large data sets or do a lot of video transcoding then 64-bit is preferable. Speed boosts can range from 10-30% over 32-bit.

---

### Post by cascade9 on 2010-11-19
> **dcstar said:**
> Are people **still** using 32-bit?!?

Seriously, I have been using 64-bit Ubuntu for about 3 years now and the only annoying issue is Adobe not having a released 64-bit Flash plugin at the moment (but they keep promising.....)

There is a 64bit linux flash plugin avaible now. Its only a 'preview', but its there, and works as well as flash ever does. 

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

> **Bitrate said:**
> I chose to go 64-bit for Linux because it's mature and well supported (mostly, baring some codec issues). If you work with large data sets or do a lot of video transcoding then 64-bit is preferable. Speed boosts can range from 10-30% over 32-bit.

Over 30% is possible. 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by amauk on 2010-11-19
Speed increases are hugely dependant on what you're doing, but generally 64bit will be faster

There's even some huge differences
The radix sort algorithm gets a 60+% performance increase going from x86 to x86_64

But most of this speed increase has nothing to do with the register width

More, the x86 architecture is notoriously short changed when it comes to CPU registers compared to other architectures. There just aren't that many of them, so algorithms that need a lot of them (Eg. the radix sort) have to do a lot of in-memory copying and general fudging around to get things done

x86_64 has many more CPU registers, so the speed increases come from not having to constantly move data around in memory

---

### Post by pme 72 on 2010-11-19
Here is a link to a discussion started in July when it was noted "64-bit Ubuntu Desktop: Not recommended for daily desktop usage" was included on the Ubuntu download page. The message was changed when Maverick 10.10 was introduced.

[http://ubuntuforums.org/showthread.php?t=1526391](http://ubuntuforums.org/showthread.php?t=1526391)

Interesting reading. I opted for the 32 bit install of Lucid as a result of the message after having installed the 64 bit since beginning with Gutsy Gibon 7.10. Have not reached any personal conclusions either way. So far the only issue I have encountered is an old large MS Power Point Presentation does not seem to want to play in 32 bit versions of Ubuntu. When it loads it takes up just over 3 GiB of ram. It will open and play in 64 bit versions even when running from a Live CD.

---

### Post by sdennie on 2010-11-20
I was a long time holdout when it came to 64-bit.  For years I ran 32-bit with a PAE kernel because I didn't want to deal with the "hassles" of 64-bit.  With 10.04, I took the plunge and went 64-bit.  After 7 months, I agree with the comments above in that you won't notice a difference except with the possibly dubious nature of the out of the box Flash experience.  That's easily fixable though.

I even recently dug out my Neverwinter Nights CD's and the 32-bit linux client runs flawlessly on 10.04 64-bit.

---

### Post by dcstar on 2010-11-20
> **cascade9 said:**
> There is a 64bit linux flash plugin avaible now. Its only a 'preview', but its there, and works as well as flash ever does. 

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
.........

Thanks for that info, I was waiting for the official release since they stopped the beta plugin development.

I've just installed that one so I'll see how it goes.

---

