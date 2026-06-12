---
title: "Internet connection issues"
date: 2010-04-12
forum: General Help
---

### Post by gatordude on 2010-04-12
I am having the same issue. I recently put a new system together.
Athlon II 630 
4G of ram
Ubuntu 9.10 (32 bit version)
Integrated HD3300 (running FGLRX) I have ATI Catalyst installed.


Everything was fine for about 2 weeks then the last few days it started to stall loading pages (FF and Chrome).
I run HTop to see if something is hogging the resources and all seems normal.

As far as I can tell I have all of the latest updates.

There does seem some weird things happening. If I start from Google.com I can navigate semi normal. If I try loading a page from memory (FF or Chrome) it hangs. Sometimes it freezes the whole system and I have to do a hard reboot. I removed all extensions and add-ons from both FF and Chrome. I am also having issues when I play PokerTH. I can play for a little while then the connection just drops. I am on a wireless connection that was running fine. I was able to transfer huge files ( >700M ) with no problems.

Any suggestions?

---

### Post by gatordude on 2010-04-12
If anybody has any insight to how I might correct this problem could you let me know?

The issue even affects installing software from the repositories.
If this is related to a bug in the latest update it would be good to know.

Cheers

---

### Post by gatordude on 2010-04-12
OK,

After checking my kernal and seeing that it should be stable and seeing a post or two about problems with mice I tracked down another mouse (my original mouse used with my PC that died)

I had a Logi Tech LX7 and replaced it with my Logi Tech MX100 and my connection problems seemed to go away????

I used the same USB port as with the old mouse.

Any ideas??

---

### Post by gatordude on 2010-04-13
Boy did I pat myself on the back too soon.
My problem is coming back, slowly.

I have Bmon (Bandwidth monitor) running and when I navigate through CNN when I click on a news item it just stops. It really doesnt matter what website it is.

HTop does not show any resource hog. I still have over 1.6G free ram and the CPU's are not loaded past more than 33%.

Any ideas?

---

### Post by gatordude on 2010-04-17
> **gatordude said:**
> Hey,

If your problem is related to Flash don't read any further.
If the problem you have is the same as mine read these posts.
My browser (didn't matter which one) got hung all the time and I could do a few things (band aide or whatever) but when I changed the MTU setting in my router I have been stable for the last two days with seamless web browsing. I came from a cable BB area to a DSL only area and all of my Windows machines were not affected by this at all. 

[http://ubuntuforums.org/showthread.php?t=1446791&highlight=connection+hangs]("http://ubuntuforums.org/showthread.php?t=1446791&highlight=connection+hangs")

[http://ubuntuforums.org/showthread.php?t=1376506]("http://ubuntuforums.org/showthread.php?t=1376506")

I changed the MTU setting in my router from 1500 to 1492 and I have had no issues.

I just wanted to share the info. I hope this helps...

:-)

---

