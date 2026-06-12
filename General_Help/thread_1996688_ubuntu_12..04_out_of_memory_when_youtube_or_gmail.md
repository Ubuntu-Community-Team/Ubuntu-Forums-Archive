---
title: "ubuntu 12..04 out of memory when youtube or gmail"
date: 2012-06-04
forum: General Help
---

### Post by Gatemaze on 2012-06-04
Hi,

I have ubuntu 12.04 64bit installed. I noticed that when I play videos or access my gmail after while my memory is to the limit. This occurs with both firefox and chrome under both unity and latest gnome. anyone else suffering from similar symptoms? thanks.

---

### Post by Slim Odds on 2012-06-04
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by 3Miro on 2012-06-04
Does your computer slow down or crash? If not, then everything is working as intended and you can just lean back and relax. Or alternatively you can read about Linux memory management.

---

### Post by pqwoerituytrueiwoq on 2012-06-04
are you getting that as a error message?
how much ram does your system have?

---

### Post by mcduck on 2012-06-04
> **Gatemaze said:**
> Hi,

I have ubuntu 12.04 64bit installed. I noticed that when I play videos or access my gmail after while my memory is to the limit. This occurs with both firefox and chrome under both unity and latest gnome. anyone else suffering from similar symptoms? thanks.

How much RAM does your computer have, and what tool are you using to check the memory usage?

Try viewing some videos and then run "free -m" in a terminal and read from the "+/- buffers/cache" -line to get the real values for how much memory is used by your programs and how much is still available for them.

As unused memory would simply be wasted, Linux uses all RAM not used by system or programs to cache recently used data in case it's needed again. This improves performance as getting the data from RAM is much faster than having to read it from hard drive. And as any of the cached data can simply be dropped when some program needs more memory, this part of RAM  still counts as free from any program's point-of-view.

---

### Post by Gatemaze on 2012-06-05
Thanks all for all your suggestions. Much appreciated. Quickly replying to some of the issues that might give you more info. The memory in my system os 2GB (should be enough), the system does not crash but becomes very laggish (I assume because it exchanges data with the swap). I quickly can see that RAM is to the limit from the system monitor applet I am running. As said this occurs with youtube/gmail after a random period of time, maybe 30mins maybe a couple of hrs (and there are only 2-3 tabs open), so my suspicion is that there is something between flash and ubuntu 12.04 64bit. My suspinsion is further enchanched by the fact that previously it was running 10.04 32bit without issues. Other systems with the same specs running 10.04 and 11.10 64bit have not shown such symptoms. I will post more info the next time this happens. Thanks again for the info.

---

### Post by 3Miro on 2012-06-05
Sluggish system, swap being used and full RAM in the memory applet are both signs of what is called "memory leak". It is a type of a BUG. Unfortunately, those are hard to pinpoint.

If you have the time, you can try to isolate the program that is causing the issue. Try rebooting and leaving the system alone, then see if there is a memory leak or not. Then run just the browser with no pages open. Then try only one page. A page with or without flash. You can also try another browser, both Firefox and Chromium are pretty powerful browser and should serve most people's needs and you can also install Google-Chrome.

Unfortunately, if you find the culprit program, all you can do is file a bug report and wait for an update. However, in the mean time, you can avoid using this program or if you do use it, then restart it often.

Gmail does not use flash, if gmail causes a memory leak

---

### Post by idoitprone on 2012-06-05
> **Gatemaze said:**
> Thanks all for all your suggestions. Much appreciated. Quickly replying to some of the issues that might give you more info. The memory in my system os 2GB (should be enough), the system does not crash but becomes very laggish (I assume because it exchanges data with the swap). I quickly can see that RAM is to the limit from the system monitor applet I am running. As said this occurs with youtube/gmail after a random period of time, maybe 30mins maybe a couple of hrs (and there are only 2-3 tabs open), so my suspicion is that there is something between flash and ubuntu 12.04 64bit. My suspinsion is further enchanched by the fact that previously it was running 10.04 32bit without issues. Other systems with the same specs running 10.04 and 11.10 64bit have not shown such symptoms. I will post more info the next time this happens. Thanks again for the info.

you need swap
do you have swap

because 2GB is not alot of ram for a modern desktop and browser
you should have 2GB-4GB of swap\

older ubuntu uses less ram

---

### Post by Gatemaze on 2012-06-06
> you need swap
do you have swap

Yes there is a 2gb swap. Slagginess is caused from exchanging data with the swap.

> Gmail does not use flash, if gmail causes a memory leak
I think it does use as when the flash plugin crushes there is a notification on all the tabs that require flash and this includes gmail.

> If you have the time, you can try to isolate the program that is causing the issue. Try rebooting and leaving the system alone, then see if there is a memory leak or not. Then run just the browser with no pages open. Then try only one page. A page with or without flash. You can also try another browser, both Firefox and Chromium are pretty powerful browser and should serve most people's needs and you can also install Google-Chrome.

If you had a look on my original post then you will see that it says:

> I have ubuntu 12.04 64bit installed. I noticed that when I play videos or access my gmail after while my memory is to the limit. This occurs with both firefox and chrome under both unity and latest gnome

---

### Post by 3Miro on 2012-06-06
> **Gatemaze said:**
> 
I think it does use as when the flash plugin crushes there is a notification on all the tabs that require flash and this includes gmail.


Install FlashBlock addon for Firefox or Chromiuma/Chrome and see if Gmail still gives you hard time. If it is flash, then FlashBlock should help a lot.

---

### Post by Gatemaze on 2012-06-25
Thanks all for your suggestions. The 'solution' I tried was to install xfce. After running my system for a few days and with the typical use it seems to be OK. Don't think it makes sense why, other than it might be a bad combination of gnome3 or unity with flash? Nevertheless, seems to be working now, so thanks again.

---

