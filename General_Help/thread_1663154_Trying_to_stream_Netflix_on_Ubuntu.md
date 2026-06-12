---
title: "Trying to stream Netflix on Ubuntu"
date: 2011-01-09
forum: General Help
---

### Post by hansolo4949 on 2011-01-09
Hello, i'm running Ubuntu 10.10, and i'm wondering if I can stream Netflix from Ubuntu. I know there are workarounds, and I will be more than happy to try them. Does anyone have a solution?

hansolo4949

---

### Post by CharlesA on 2011-01-09
The only real "workaround" I've seen is to run Windows inside a Virtual Machine, or dual boot.

---

### Post by hansolo4949 on 2011-01-09
Thank you, charlesa. I am dual-booting windows and Ubuntu, but I heard that there's a way to "fake" your os in a browser so that netflix will allow you to stream.

Any other suggestions?

hansolo4949

---

### Post by CharlesA on 2011-01-09
As far as I know it's been tried before and hasn't worked.

---

### Post by hansolo4949 on 2011-01-09
Ah, okay. But i'm sure someone has been able to stream netflix using SOME method, I just wish they find this thread and tell it ;)

hansolo4949

---

### Post by CharlesA on 2011-01-09
This comes up every now and then. This is easier then posting a link to each thread:

[http://www.google.com/#sclient=psy&hl=en&q=netflix+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=83f87efc6f926f13](http://www.google.com/#sclient=psy&hl=en&q=netflix+site:ubuntuforums.org&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=83f87efc6f926f13)

---

### Post by hansolo4949 on 2011-01-09
Thanks for the link charlesa! It looks like you're right, the only way to stream Netflix in Ubuntu is to use a Virtual Machine. But that kind of defeats the propuse of Ubuntu, right? Why should we have to use a virtual machine to stream Netflix? Maybe that can be fixed in 11.04, or an application to stream netflix?

Just a thought.

hansolo4949

---

### Post by CharlesA on 2011-01-09
It doesn't really defeats the purpose of running Ubuntu. It's kind of the same thing as trying to a Windows application in WINE and having it not work. It wasn't coded to Linux and you are trying to make it work by tricking it into thinking you are running it on a Windows box.

I think the reason Netflix doesn't work on Linux is that it has to do with Silverlight and Linux not supporting it. I know there is Mono, but I'm not sure of all the details outside of it just not working.

---

### Post by efflandt on 2011-01-09
An alternative is to simply use a device that supports streaming Netflix HD (BluRay player, Roku box, or HDTV w/networking).

My old PC was not fast enough to stream Hulu 480p content full screen @ 720p without dropping frames (much less full screen 1080p) and did not have a BluRay player, so I got a separate BluRay player that does Netflix.  Also I heard that Netflix HD does not do 720p anyway on a PC, like it does on a dedicated device.  The 32" 1080p HDTV I use as a monitor has 4 HDMI inputs (plus VGA), so connecting other devices is not a problem.

My new PC does great displaying 64-bit Hulu Desktop w/real 64-bit flash, full screen on 1080p HDTV.  But streaming Netflix uses Silverlight with some sort of copy protection that is difficult to crack.

---

### Post by hansolo4949 on 2011-01-09
Okay, thank you both for your replies! doesn't the current version of moonlight (or the beta) work with netflix as long as you can get past Netflix not liking Ubuntu?


hansolo4949

---

### Post by d5xtgr on 2011-01-09
I believe even the recent iteration of Moonlight isn't adequate (I've certainly had no success with it).  The issue is its support of the licensing method Netflix uses if I am correct; obviously cracking the rights management code is designed to be an obstacle.

I've been able to get on both chrome and firefox to the point where netflix assumes there's an error with its own server and urges you to contact support but I rather doubt they'd be sympathetic.

---

### Post by coreyinprogress on 2011-02-20
> **d5xtgr said:**
> I believe even the recent iteration of Moonlight isn't adequate (I've certainly had no success with it).  The issue is its support of the licensing method Netflix uses if I am correct; obviously cracking the rights management code is designed to be an obstacle.

I've been able to get on both chrome and firefox to the point where netflix assumes there's an error with its own server and urges you to contact support but I rather doubt they'd be sympathetic.

So, I was just checking in on this old debate, and had to go dig up my log-in (my last post was in.....08? damn)

The last time I googled the hell out of this I read a developer for netflix posting in a forum (can't find it now...sorry).  He pretty much pointed everything back eventually to our good old buddy Microsoft.  

The studios see microsoft as the most business friendly, so netflix is contractually obligated to use their codec.  Nothing linux, netflix, or moonlight can do will get around the damn DRM.  Moonlight could get every function of the web platform right, but short of MS doing something, no dice.

I saw somebody working on emulating a Wii....

---

### Post by jerenept on 2011-02-20
Boxee? I think it has Netflix support? (not sure) [http://boxee.tv](http://boxee.tv)

---

### Post by kb2001 on 2011-02-20
I believe the limitation of Moonlight being able to support Netflix has to do with the absence of the DRM support in Moonlight.  Netflix uses the DRM in Sliverlight, MS won't allow it for Moonlight.  No end in sight to this problem.  Netflix needs to use the DRM to get movies to stream, studios won't let them do it unguarded anymore.

So, look to MS and their refusal to include the DRM support in the open source silverlight player.

---

### Post by hansolo4949 on 2011-02-21
Thank you all for your detailed replies! I have laid my issue to rest by using a VM which provides bad results, but at least streams smoothly. DRM us a very touchy subject, and I do nit like it one bit. Why inconvenience millions of people so a comparatively small amount of people cannot redistribute the media illegally? I see (somewhat) the justification in Netflix's case, but yeesh.....



Edit: I can stream Netflix on Windows 7 using Dual boot, and stream it from several other devices, so this isn't necessary, It would just be convenient. After all, don't we all dream of the computer/htpc that can do everything you want it to do without having to use Windows, and in an indirect way, try not to support them?  I do not know why Microsoft has to rain on our parade by removing that from moonlight.

---

