---
title: "OCZ Vertex 2 on 10.04?"
date: 2011-01-27
forum: General Help
---

### Post by lukemk1 on 2011-01-27
So I have a few general questions on how I should go about setting my SSD up. I have read various articles about using the "discard" option is fstab for TRIM. I also read to include the "noatime" option so the filesystem does not record access times.

I know that I should have the swap somewhere else. I'm just planning on using this to contain the / and /boot partitions while keeping my /home and swap on the current hard drive they are on.

My questions are what filesystem should I use?
What options should I use in fstab?
And is my partitioning scheme fine or should it be changed to some other method?

Any other other helpful comments on this would be greatly appreciated.

---

### Post by lukemk1 on 2011-01-27
Bump.

---

### Post by piquat on 2011-01-27
Hello,

I have the same drive in a new build, the one in my sig.  I did a bit of reading and from what I understand, and what seems to work on this system, you need three things for it to work.  One of them is kernel 2.6.33 or higher.  HOWEVER, I've also read that this drive, with the 1.5 firmware or above will do it itself.  This I question.

I have both 10.10 and 10.04 on this drive (Mint really but it runs the 10.10 kernel).  If I go here:
[http://andyduffell.com/techblog/?p=852](http://andyduffell.com/techblog/?p=852)
and follow the instructions to see if it's working, it passes the test in 10.10 but not in 10.04.  I have the discard option in the 10.04 fstab also.

I will say, this is my first SSD so there may be something else I could be doing to get it working in 10.04.  

And if you go reading on this subject keep in mind most information you read that's over a year old is outdated.  There is also a Linux section to the OCZ forums that's very helpful.

---

### Post by lukemk1 on 2011-01-27
I know about the kernel requirements (I have my own 2.6.37 compiled). That link is almost identical to another thing I read, but I've also read something about using the "noatime" option in fstab, do you know anything about that?

Okay, I will check those forums out.

---

### Post by piquat on 2011-01-27
Yes, I have noatime set also.  The discard option is what really does the automatic TRIM.  noatime really just cuts down excessive writes.

discard and notatime are the only two I have set.  If you have the .37 kernel and 1.5 firmware it should pass that test.  If it's working... well, it's working.   :)

You should also look into wiper.sh if you have need to TRIM manually. That's also something that's covered on the OCZ forums pretty well.

---

### Post by lukemk1 on 2011-01-27
Alright I will use both options then. Could you show me one of the lines in your fstab? (I want to make sure I know how the format is supposed to be)

I saw stuff about wiper.sh on the forums, I shouldn't need that as long as I pass the trim test though correct?

---

### Post by piquat on 2011-01-27
```
UUID=63564e46-2894-4de8-a7fb-1f073e5148ed /               ext4    discard,noatime,errors=remount-ro       0       1

```The options are just comma seaparated but no spaces.

These are pretty smart drives.  Once I knew I had TRIM running I didn't get too option happy.  They've come quite a ways in the last year and a half or so.  It's the main reason I put one in this last build.


Edit:  The only other thing to watch concerning an SSD is partition alignment.  The Win7 and the 10.10 installer will do this automatically.  Just something to take a peek at to see if it was done properly after the install.  I'm not the person to ask about that, I'm not quite solid on that one yet.

---

### Post by lukemk1 on 2011-01-27
Thanks for the code.

Regarding alignment, does 10.04 do it automatically as well? Because that is what I'm planning on using.

Also I checked my firmware (using disk utility) and it is at v1.27, I then checked the site and the newest for the drive is v1.28 so I'm confused with when you said check to make sure it is 1.5 (or higher) because I don't see that firmware anywhere...

---

### Post by lukemk1 on 2011-01-27
Bump.

---

### Post by piquat on 2011-01-28
> **lukemk1 said:**
> Thanks for the code.
 
Regarding alignment, does 10.04 do it automatically as well? Because that is what I'm planning on using.
 
Also I checked my firmware (using disk utility) and it is at v1.27, I then checked the site and the newest for the drive is v1.28 so I'm confused with when you said check to make sure it is 1.5 (or higher) because I don't see that firmware anywhere...
 
Everything I read and what was born out on my drive says no.  My 10.04 is aligned kind of by luck.  You can do it manually but here's what happened in my case.
 
I installed Win7 at the start of the drive, it's aware (skynet anyone?) so it alignes itself properly and ends it's partition in the correct place (one short of where the next one should start).  I installed 10.04 next and it just picked up where 7 left off which means it started in the right place but I can tell it's not aware of this because it ended in the wrong place.  That really doesn't matter, as the vast majority of that parition is aligned excepting the little chunk at the end, which can be ignored.  Then I left a big gap for a shared NTFS partition and installed Mint at the end of the drive and it's aligned properly because it's aware. 
 
Don't ask me how to align a partition manually.  It looked a bit deep and since mine aligned automatically, I stopped reading.

---

### Post by lukemk1 on 2011-01-28
Do you know how to check if it is aligned properly? And is it completely necessary to make the SSD aligned properly or is it just a benefit?

Also could you answer the firmware question? I'm not really sure if disk utility is wrong (which I honestly doubt), if I'm looking in the wrong place, or if 1.27 is 1.5? I really just don't understand it at all.

---

### Post by piquat on 2011-01-28
> **lukemk1 said:**
> Do you know how to check if it is aligned properly? And is it completely necessary to make the SSD aligned properly or is it just a benefit?

Also could you answer the firmware question? I'm not really sure if disk utility is wrong (which I honestly doubt), if I'm looking in the wrong place, or if 1.27 is 1.5? I really just don't understand it at all.

IIRC, you look at the point the partition starts with fdisk.  Divide that number by 512.  I don't remember how that was supposed to come out though.  I'm on my laptop right now at work.  I'll poke around a bit on that machine in the morning to see if it refreshes my memory.  And "completely necessary"?  No, you could run without it, but it will slow things down due to write amplification.  If that's actually the 10.04 installer, good luck.  LOL  Reading about manually aligning partitions gave me a headache!  I'm glad I found a way around it...

It seems you are correct about the firmware.  I remember 1.5.  I didn't put much thought into this either as I pretty much went straight to the testing after adding discard and it passed the test so I stopped poking it in the side.  Once again, if I write that test file, remove it and sync, and I get all zeros back when looking at that portion of the drive, I'm happy.

At this point, I don't even want to know if I have the latest firmware.  If I don't it's going to bug me, and I really don't want to mess with firmware on a drive housing a running system.

---

### Post by piquat on 2011-01-28
This should help you out with partitioning.  I think it's what I used:

[http://www.ocztechnologyforum.com/forum/showthread.php?77769-A-Simple-How-To-on-Partitioning-and-Alignment-on-GNU-Linux-using-fdisk](http://www.ocztechnologyforum.com/forum/showthread.php?77769-A-Simple-How-To-on-Partitioning-and-Alignment-on-GNU-Linux-using-fdisk)

From that guide:

> [SIZE=4]Alignment (Part 2 - the rule)[/SIZE]

Ahhh. Alignment. How crazy it is I loathe you. It's pretty easy and much  easier once you know the practice behind partitioning using sectors.  It's gonna be a walk in the park. I promise. When it comes to alignment,  you only need to keep 1 rule in your head. The starting sector **must be divisible by 512 evenly (no remainder)**.  It does not matter the size of the partition or where that partition  ends. All that matters is that the partition you create starts on a  sector divisible by 512 (evenly).

Can you believe it? Could it really be that simple? You can devise a  perfect GB.MB solution for a partition or a crazy obscure solution and  all that really matters in the end is where that partition starts.  That's it!
That guide is the top sticky in this forum:
[http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-OCZ-SSD-Support-for-Linux-and-Apple-OSX](http://www.ocztechnologyforum.com/forum/forumdisplay.php?237-OCZ-SSD-Support-for-Linux-and-Apple-OSX)

Really, pay attention to that site.  Guides on there are pretty good.  I'm so far from a guru I'm happy to get my shoes tied in the morning.  LOL

---

### Post by lukemk1 on 2011-01-28
I suppose what I could do to make sure the partitions are aligned is use the 10.10 installer to partition the drive, then switch to 10.04 to use the partitions for the install, huh?

Maybe OCZ has recently changed the firmware version numbering or something... although that would be really annoying for people that were used to the older style.

I just read that forum a bit ago and found that. Thanks though.

EDIT: I have just partitioned them manually using fdisk. It actually wasn't too bad so now that my partitions are aligned I'm going ahead with installing 10.04 on it and then making sure TRIM is working.

---

### Post by piquat on 2011-01-28
Haha, I never thought of that!  That's a pretty good I idea.  I'll have to remember that one.

I'm kind of curious if that kernel is going to TRIM even though it's 10.04.  It should but you never know.

---

### Post by lukemk1 on 2011-01-29
Okay, well I got it up and running but I had a graphics driver issue while using 2.6.37 under 10.04 so I just moved up to 10.10 for the time being since by default the kernel supports TRIM & I don't have graphics issues. 

What I am planning on doing is waiting until the 10.04.2 release comes out and seeing if the kernel is .33+ (Which I'm hoping it is) if it isn't then I will just have to try compiling 2.6.36 or lower that way I don't have the graphics issues (or just wait until they are solved).

At any rate, thanks so much for your help!

---

### Post by piquat on 2011-01-29
You're welcome, glad to help out.

> **lukemk1 said:**
> What I am planning on doing is waiting until the 10.04.2 release comes out and seeing if the kernel is .33+
That may be the solution for my 10.04 install also.  I don't like to use it much really.  Either .33+ or I need to go back to reading about wiper.sh.


Anyway, good luck!

---

### Post by lukemk1 on 2011-01-29
yeah, I prefer 10.04 to 10.10 too. I actually just solved my issue by installing a backport of the .35 kernel (which is used on 10.10) onto 10.04 and now everything is working perfectly under 10.04. =P

This is the link if you are interested: [https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway](https://sites.google.com/site/lightrush/random-1/howtoinstalllinuxkernel2635onubuntu1004lucidfromubuntu1010mavericktheeasyway)

---

