---
title: "Live CD without HDD?"
date: 2009-10-02
forum: General Help
---

### Post by alykotah on 2009-10-02
I recently re-attempted to migrate over to Linux.  Having tried it before about 13 years ago, I couldn't wrap my head around the commands having been raised on DOS, it seemed so foreign to me. IMO xfree(I think was what it was called), at the time frankly sucked.  I see it's come along way, and is more the flavor I'd like.  Just plug it in and go.   

I had recently set up an old computer (500mhz) for my son who is 4yrs old.  I had it loaded with educational programs such as reader rabbit, and such.  The problem was no matter how much I tried to  limit access to anything but shortcuts to his programs he always found a way to botch the system up.
Now looking at a LiveCD I'm thinking this is a perfect solution.  Because even if he does get into something he won't be able to change the files.

Ultimately I'm thinking if possible, I would create and mount ISO's of his program CD's with the Ubuntu LiveCD and burn it to a DVD or maybe a 4gb thumb drive.  Following this up with permanent links on the desktop to his games.  The idea being to make it so that he can't accidentally delete his links, resources, or changing settings permanently.  So that anything that would get messed up would simply be fixed with a reboot.

So finally getting back to my question, is it possible to boot the livecd without a HDD?  I'm looking to mount the computer in a custom enclosure, and the less that I need to stuff in there the better.  I did read where the LiveCD will work in conjunction with a USB stick for persistence. In fact I would find it even better if I could just run it off the usb drive only, and do away with the optical drive as well.  The enclosure is going to be rugged and able to take some bumps, so the less moving parts (besides fans) the better.

thanks

---

### Post by scragar on 2009-10-02
You might want to look into applications for creating your own custom liveCD, many offer you options for what you want, you just set up the system first as you want, then run the application to convert it to a liveCD, check a few boxes for options, then you're done.

LiveCDs work fine without HDs, after all everything is run from the CD, as long as you've got the ram(because you won't have a HD or swap space) there shouldn't be a problem.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by alykotah on 2009-10-02
ok, good to know.  I wasn't sure if it was going to need a ramdrive or swap area.

Thanks for your prompt (nearly immediate) reply.

---

### Post by scragar on 2009-10-02
> **alykotah said:**
> ok, good to know.  I wasn't sure if it was going to need a ramdrive or swap area.

Thanks for your prompt (nearly immediate) reply.

Depends how much ram you've got available, general rule is you need around 256MB of ram + ram used by applications.

Of course depending on the enviroment and setup you could reduce the ram requirement to almost nothing, I've seen liveCDs like knoppix that will run on 96MB of ram(requiring around 128MB to run open office).

---

### Post by snowpine on 2009-10-02
Yes; of course you can run Ubuntu Live CD without a hard drive. You can also run it from a USB thumb drive as well (if the hardware supports USB boot). 

A couple of handy tools are Remastersys (for making a custom Live CD) and Unetbootin (for making a Live USB).

It doesn't sound like persistence is what you want; that would allow him to make changes. :)  Good luck!

---

### Post by jward3010 on 2009-10-02
> **alykotah said:**
> The problem was no matter how much I tried to  limit access to anything but shortcuts to his programs he always found a way to botch the system up.

Maybe at the time you we're logged in as root, the good aspect of Ubuntu and most modern desktop based linux distro's is the way in which you're logged in purely as a user account, you can't log in as root even anymore (probably with a bit of tinkering no doubt you can). Hence, you can't go into /bin or /boot etc. and delete the files easily, you need root access and typically have to do it through the command line which adds an extra layer of difficulty to a novice user. So I'd say forget the LiveCD idea and try an install, just don't give your son the root password. The only files he can mess up are his own under /home and there not fundamental to a working system. 

To begin with I found it restrictive in fact (I was used to direct root login under Slax etc.), now I find it brilliant and completely workable. I wish all systems we're done this way.

---

### Post by alykotah on 2009-10-02
Actually I had his comp setup before with xp,  his acct was limited, and even with removing all his desktop icons except for ones I wanted him to have, there was still too much he could get into with the start button.

I like the idea that even if he get's into settings it's all resolved with a reboot.  Not so simple with xp, before I had to dig to see what he had done.  

Thank you all for your help.  I know the suggestions will come in handy as this project progresses.

---

### Post by jward3010 on 2009-10-02
He's obviously ridiculously curious, which to be honest is fantastic. 

Give him a machine he can destroy and see if he tries to fix it as well - or does not like that part of it?

---

