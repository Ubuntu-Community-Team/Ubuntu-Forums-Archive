---
title: "Is it safe to disable IPV6 in Firefox about:Config?"
date: 2009-12-04
forum: General Help
---

### Post by JoeyF on 2009-12-04
What does it do?


Thanks,

---

### Post by Sam on 2009-12-04
It just disable IPv6. No more, no less. Don't worry, it's safe.

---

### Post by JoeyF on 2009-12-04
I mean, What does IPV6 do?


Thanks.

---

### Post by Sam on 2009-12-04
[quote=Wikipedia]Internet Protocol version 6 (IPv6) is the next-generation Internet Protocol version designated as the successor to IPv4, the first implementation used in the Internet and still in dominant use currently.[/quote]

Details: [http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)

---

### Post by JoeyF on 2009-12-04
One last question.

I heard that it is replacing IPV4 and that it will be/is necessary, Is that true?



Sorry,

---

### Post by Sam on 2009-12-04
Yes, it will replace IPv4 (that's its purpose), but it won't happen soon, since ISPs and hardware manufacturers are not willing to change.

---

### Post by JoeyF on 2009-12-04
And is there any other ways to speed up Ubuntu?

Since it seems IPV4 is just a short term fix

---

### Post by wilee-nilee on 2009-12-04
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

The fasterfox addon will do basically the same thing.

---

### Post by JoeyF on 2009-12-04
Any ways to make Ubuntu itself faster?

I already did FF Pipelining

Thanks,

---

### Post by wilee-nilee on 2009-12-04
Tell us your computer specs it may be a little more ram is needed. Sorry I missed the Ubuntu faster.

---

### Post by JoeyF on 2009-12-04
> **wilee-nilee said:**
> Tell us your computer specs it may be a little more ram is needed. Sorry I missed the Ubuntu faster.


It's an Emachine W3650 dual booted with XP, It runs XP fast though. Ubuntu sometimes lags a little.

---

### Post by wilee-nilee on 2009-12-04
Is karmic a upgrade or fresh install, I ask because ext4 seems to be a faster running setup. I had XP on a netbook and even with 2 gigs of ram it ran slow compared to Jaunty and Karmic.

---

### Post by JoeyF on 2009-12-04
> **wilee-nilee said:**
> Is karmic a upgrade or fresh install, I ask because ext4 seems to be a faster running setup. I had XP on a netbook and even with 2 gigs of ram it ran slow compared to Jaunty and Karmic.

I went from 8.10, To 9.04, To 9.10.

---

### Post by wilee-nilee on 2009-12-04
> **JoeyF said:**
> I went from 8.10, To 9.04, To 9.10.

All upgrades I suspect, a fresh install or changing the partition to ext4 would help. If you change the partition though your going to have to back up so a fresh install is easier for many. Have you downloaded a ISO of Karmic, if you put it on a thumb with usb creator it will give you a look at it running about the same speed as installed. Karmic on a thumb runs at the same speed as my installed Karmic which runs faster then W7 in general.

Also how full is the partition this will slow things down as well.

---

### Post by JoeyF on 2009-12-04
Say again?(The USB speed part)

I know i didn't give Ubuntu that much space when i first dual booted it.

My hard drive is 160G(Including Windows)

I plan on eventually installing Ubuntu over XP. Would that help?

---

### Post by wilee-nilee on 2009-12-04
> **JoeyF said:**
> Say again?(The USB speed part)

I know i didn't give Ubuntu that much space when i first dual booted it.

My hard drive is 160G(Including Windows)

I plan on eventually installing Ubuntu over XP. Would that help?

Go to applications accessories disc usage analyzer and it will tell you how much space is left in Ubuntu. 

So is this a dual boot or a wubi install. 

If it is a wubi Ubuntu runs slower anyway.

If it is a dual boot then you have 2 independent partitions so just having Ubuntu wont change the speed. 

There is a thumb loader in system administration called usb startup disc creator this allows you to load the ISO onto a thumb drive and have a persistent file that allows you to update and add programs and have a persistent bootable thumb.

I suspect you have a combination of reasons why Ubuntu seems to run slow so if you can confirm the type of install wubi or dual boot and is it a upgrade rather then fresh install, and how much disc space you have left in Ubuntu.

---

### Post by JoeyF on 2009-12-04
22.6 GB available. Any way i can add more?


It is dual boot BTW.

Thanks for your help.
:)

---

### Post by wilee-nilee on 2009-12-04
> **JoeyF said:**
> 22.6 GB available. Any way i can add more?


It is dual boot BTW.

Thanks for your help.
:)

I think you could shrink the xp and expand Ubuntu into the space but I'm not sure. If it was me and you wanted to keep the dual boot I would shrink the XP to where you want it defrag it first though and then do a fresh install of Karmic if it has been a continuous upgrade in the deleted Karmic partition space.

Karmics release was best approached with a fresh install due to partition type changes and the grub2 change. Karmic should theoretically be blowing away XP.

---

### Post by JoeyF on 2009-12-04
So i can just pop in a Karmic DVD, And replace the current Ubuntu partition with it without removing XP?

I may just wait until i buy a new router(Then i am going to do a complete Ubuntu install)

---

### Post by wilee-nilee on 2009-12-04
> **JoeyF said:**
> So i can just pop in a Karmic DVD, And replace the current Ubuntu partition with it without removing XP?

I may just wait until i buy a new router(Then i am going to do a complete Ubuntu install)

You would want to use the Live CD to delete the Karmic partitions with gparted leaving a open space then choose the install in free space with the partition GUI in the install.

You might also consider buying the upgrade to W7 it is a pretty fast OS but I think having 2 gigs of ram will be helpful with W7 and Ubuntu which doesn't really need that much unless you have a virtual machine. I found everything sped up when I went from 1 to 2 gigs ram on my netbook though. 

I only have W7 due to a student upgrade of 29$ I would never have bought it otherwise and only had XP because it came installed in the netbook. W7 is not bad though if I had started my computer usage on W7 rather then 3 years ago with Linux I probably would just use W7. But I started with Linux so the MS stuff feels like playing an old game of pong as far as figuring it out. With only a short time of using MS I have fixed several friends MS setups that were running slow due to malware...etc and not being set up with the least amount of startup apps needed, and installing a better disc cleaner then the stock MS one.

---

