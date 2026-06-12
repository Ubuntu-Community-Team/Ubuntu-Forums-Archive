---
title: "IBM ThinkPad R32 very poor performance"
date: 2010-02-08
forum: General Help
---

### Post by mmillman on 2010-02-08
Hello,

I'm trying to run Ubuntu 8.10 Intrepid Ibex on an old hand-me-down laptop that I got from a family member, and I've noticed that the performance is actually much worse than it was on Windows XP Professional (32-bit).

First of all let me give you my specs:
IBM ThinkPad R32
Intel Mobile Pentium 4-M 2.0 ghz
ATI Radeon Mobility M6 (I think this is actually the Mobility Radeon 7000 IGP) with 16MB RAM
256 MB RAM (PC-2100)

I understand that these are very low performance specs, but it feels like the computer is running very sluggishly even for those specs.  The computer ran just fine in Windows XP, but is extremely sluggish in Ubuntu.  It seems like it detected all the hardware just fine, but I feel like it may not be utilizing the CPU and/or Video to the extent that it should be...

A couple of places where it really seems to struggle is when first opening new programs, viewing flash intensive Web 2.0 type webpages (i.e. YouTube), and listening to music/podcasts (With Rhythmbox).  It seems like Rhythmbox really kills my performance more than anything else, but the performance is poor all around compared to XP, and I feel like that shouldn't be the case.  

Like I said, I understand that the specs are poor, but it feels like it's not even living up to those specs...  Any help would be GREATLY appreciated.

I know that 8.10 is old and outdated now, but it's what I had laying around and I figured that it might perform better on this old deprecated laptop than 9.10 would anyway...  Am I wrong in this assumption?  Would 9.10 perform better for me?

Any help would be great... I'm quite a noob to linux (but not new to computers by any means, so I don't need things to be dumbed/watered down too much) so any more information you would want, feel free to ask and I will get it to you.

Thanks ahead of time

---

### Post by jfl on 2010-02-08
Are you running from the "Live CD" ?
It will be SLOW on any machine.
When installed on the HD it is a lot faster.
OTOH 256 RAM is marginal for Ubuntu; you might want to try xubuntu.

---

### Post by mmillman on 2010-02-08
No I installed it from the Alternate CD...  Live CD was pretty much unusable.

I know the it is very low on memory, but I can't explain it when I say it just feels like it's "underperforming".  For instance, Youtube is pretty much unwatchable, yet it performed near flawlessly in XP...  I don't feel like this should be the case.

I don't think it's a video problem (although it could be), I feel like it's a processor issue (Mobile Pentium 4-M) or possibly a chipset or APM/ACPI issue.

---

### Post by mmillman on 2010-02-12
I'm gonna bump this again, with some new info.

It seems that the problem I had with the horrendous performance was related to the apt-xapian-index package.  Whenever it was running, it was hogging 90+% of my CPU.  I've fixed this problem, but I'm still getting very poor performance in video/audio playback... especially streaming sites i.e. YouTube.

I'm going to upgrade to Karmic tonight...  If i still have these problems, I will bump this thread again with any relevant info...

---

### Post by ergosteur on 2010-09-07
Hey, any progress on this? I also inherited an old R32. Installing Ubuntu 10.04 worked fine but it's hopelessly slow. Cursor lag, constant drive activity... Feels like a Windows machine after a couple of years of use by an inexperienced user with no AV. I thought it might be the low RAM, so I tried Xubuntu, but it's not better.

Next, I guess I'll try installing Debian...

---

