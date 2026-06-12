---
title: "Acer Aspoire One and Karmic"
date: 2009-11-13
forum: General Help
---

### Post by Radioman991 on 2009-11-13
Hello:

I am searching to see who has had good and bad luck getting Karmic to run on the Acer Aspire One netbook.

Specifically, the desktop version, NOT the UNR version.

Reason:  I did a clean install on mine, and the machine was almost useless.  Screen draws were horrible...much like I experienced with Jaunty, but I was able to correct this in Jaunty with posts in the forums.  I could find no similar tweaks for Karmic on this unit.  Additionally, I was able to obtain 1366 x 768 resolution in Jaunty, but could find no tweaks to accomplish the same in Karmic.

Meanwhile, I have heard from some folks in other forums on the Internet who had no issues with Karmic on AAO's.  Hardware differences?  BIOS differences?

I was hopeful that this version would run much better on the netbook, and need fewer tweaks than Jaunty, but I was sadly disappointed.  As a user since Feisty, each subsequent release has worked better on all my various machines until now.

Thread is not intended to be flamebait, nor a trashing on Karmic...I just want it to work.  Looking for clues on how to accomplish this.

Regards,

Radioman991

---

### Post by wilee-nilee on 2009-11-13
I upgraded the XP to W7 With 2 gigs ram and Karmic runs very good, there were some problems but it was the programs I haven't had to add any drivers or file tweaks. Wireless works great now earlier on I had to use wicd with the net-book version but this wa 2weeks pre-release. W7 and karmic run pretty neck to neck in speed, but W7 is using a minimum of 600mib of ram Karmic is much less. I suspect that karmic will beat the W7 in speed shortly though. How old is the net-book mine is like a month old. Also how much ram do you have?

---

### Post by Chubby93 on 2009-11-13
Everything works great for me....except for the microphone.

I can't figure it out.

---

### Post by Radioman991 on 2009-11-13
let's see....about 2 months old...have to actually check the receipt, but close enough.

You mentioned XP and W7...you running wubi or dual boot?   Mine only runs Ubuntu.  I wiped Vista immediately after arriving home, on both mine and wife's AAO's.

Initially, I had XP on the wifes unit for a while, but ran into problems with the webcam driver.  It would not completely shut down when you wanted it to (the OS).  Found removing the Windows webcam driver fixed this.  After a couple days, finally talked the wife into letting me put Jaunty on it, and an XP virtual machine for her 1 Windows game she likes.  Hers has ran flawlessly since.  She at this time doesn't use the webcam, nor the front mic, which is an issue in Jaunty.  She also doesn't watch flash on hers, which would die (audio) in Jaunty until I upgraded the ALSA driver manually.  The resolution issue out of the box, ALSA driver, and choppy flash were the biggest tweaks I had to do under Jaunty on these units.  Kernel upgrades break the video driver usually, but I can fix this.

I was hopeful that Karmic would fix that, and with the migration to Empathy from Pidgin, we could then cam voice and video chat, but getting the OS to work first on mine has been the nightmare.  Haven't even tried to get Karmic on hers yet.  I am the "beta tester" in the house.

-pk

---

### Post by Radioman991 on 2009-11-13
Chubby:

Guess I just had a bad day or something.  Karmic was so slow on screen draws, I could SEE the screen moving left to right as it drew the login splash screen.

There is a subtle difference on the cases between mine and the wifes.  I'll try to post a pic of each tomorrow when I get home form work.  I am wondering if some AAO's have a slight difference in chipsets.

I was able to "fix"he mic in Jaunty with an ALSA driver upgrade at the command line.  Unknown if it'll work in Karmic...had to roll back to Jaunty in order to have a functional machine.

---

### Post by wilee-nilee on 2009-11-14
So the netbook came with Vista it must have 2 gigs of ram at the least. I bought a student upgarde of W7 and just wiped the computer and dual booted with W7 and Karmic. 

Now I started using computers 3 years ago at the age of 42 years old I need one for writing papers upon returning to college. There is a well known computer recycler and green disposal non profit in the city I live in so I learned about computers on a Linux setup dapper to start with.

I have used Linux exclusively until I bought the netbook a month ago I found XP to run way to slow even with 2 gigs of ram, but the W7 OS is very fast and a great improvement so, if you wanted to get the W7 upgrade for vista it is 119$ and do a fresh install and dual boot it if you can get the Linux to work. The fresh install of the upgrade though will not accept the key but you can call MS W7 tech support and they will crack it in for you. 

Actually I think you get a free update for that computer since you bought only 2 months ago. So I think you have some good options here at the least you could install the W7 a fast running OS and just go with that and or dual boot another version of Linux there are 100's of variations. or it just might be the install of I think you installed Karmic that might be bad.

---

### Post by Radioman991 on 2009-11-14
Thanks for the info, but I have no desire to ever install Windows again.  I have gotten that disgusted with MS products.  Tired of cleaning / supporting them.  I'll use the XP I have for the 3 apps I need to be able to run...and MS "outstanding" SilverBlight, to stream NCAA games to the HDTV.

-pk

---

### Post by Radioman991 on 2009-11-14
I would be curious to know what BIOS version you guys who are having no issues are running.  My box is running Version 3204 of the BIOS.  There is a 3210 out there, and if I could get the danged thing to flash, that might be a help.

-pk

---

### Post by Aearenda on 2009-11-14
The original Acer Aspire One with a 1024x600 screen runs much better with Karmic than with Jaunty for me, thanks to the improved Intel screen driver. I'm using the 3309 BIOS. 

Radioman991, the fact that you quote 1366 x 768 resolution suggests to me that yours is a more recent AA1 that has the "Poulsbo" Intel GMA500 video chipset, which requires a different driver. That driver isn't available for Karmic AFAIK, which would be why it goes so slowly.

These threads might help if this is the case:
[http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)
[http://ubuntuforums.org/showthread.php?t=1253406](http://ubuntuforums.org/showthread.php?t=1253406)

Good luck!

---

### Post by Radioman991 on 2009-11-15
Aearenda

You are correct  It is the Aspire One...the widescreen one.

Thanks for the thread links.  I will check them out.

-pk

---

