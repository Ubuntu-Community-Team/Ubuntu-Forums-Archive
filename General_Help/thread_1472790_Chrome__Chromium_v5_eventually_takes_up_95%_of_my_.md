---
title: "Chrome / Chromium v5 eventually takes up 95% of my memory"
date: 2010-05-04
forum: General Help
---

### Post by martini1179 on 2010-05-04
I'm wondering if anyone else has this problem, and if you've been able to do anything about it. 

Chrome / Chromium v5.x, when surfing for a few hours, will eventually take up to 95% of my system's ram, and I have 4GB. When this happens, even closing a lot of tabs only frees up a few percentage points of my system memory. True, I have a lot of tabs open and my browser sessions can last several hours, but it didn't used to be this way with v4. This problem started soon after Chrome/Chromium v5 came out, and exists for me in both Karmic and Lucid. 

And yes, I'm sure that this is Chrome / Chromium causing this, since I don't usually run anything else simultaneously with Chrome.

---

### Post by Portmanteaufu on 2010-05-04
What tool are you using to monitor your system memory? Is it something that specifically calls out Chrome for using all the memory, or are you just seeing all your memory marked as being in use? If it's the latter, there's a very reassuring explanation as to what's going on, but I'll hold off until I know that's the case.

---

### Post by Portmanteaufu on 2010-05-04
To help us diagnose potential problems, could you please post the output of:

```
free -m
```

---

### Post by martini1179 on 2010-05-04
> **Portmanteaufu said:**
> What tool are you using to monitor your system memory? Is it something that specifically calls out Chrome for using all the memory, or are you just seeing all your memory marked as being in use? If it's the latter, there's a very reassuring explanation as to what's going on, but I'll hold off until I know that's the case.

I usually use system monitor to determine system memory usage. However, I sometimes do check both Chrome's task manager. 

I'm really interested in the "very reassuring explanation." 

I'll run the terminal command the next time I see all of my memory being taken up.

---

### Post by Portmanteaufu on 2010-05-04
Unfortunately, I'm not too familiar with the workings of System Monitor. (I'm more of a command-line guy, m'self. :) )

With a lot of utilities that show system-wide RAM usage, the number that is displayed as "free memory" is often alarmingly low. However, this is because of a feature in Linux's memory management procedure.

RAM is ~100 times faster than your hard drive -- for that reason, it is always desirable to have the information you want stored in RAM. So, in an attempt to be helpful, Linux keeps lots of information that you've needed in the past in RAM as a cache. This memory is not exactly "in use" because it would be overwritten if the space was needed. But it's not exactly "free" either, so it doesn't show up as such. As a result, people will often look at the tiny amount of RAM labeled "free" and blame Linux for being inefficient with its memory, when in reality it's quite the opposite.

When you run 'free -m', the column marked 'free' on the row marked '-/+ buffers/cache' is the actual number of megabytes of RAM that are available. (Truly free RAM + RAM used as cache.)

In your case, however, it sounds as though this problem might truly be specific to the program you're running. If System Monitor gives per-process information, look and see what it reports Chrome's memory usage as being. (Alternatively, you could run 'top'.) If it's over a couple hundred megabytes, that's a pretty solid red flag.

---

### Post by zaphod777 on 2010-05-04
are you running the dev version of Chrome of the beta?

---

### Post by martini1179 on 2010-05-10
> **Portmanteaufu said:**
> Unfortunately, I'm not too familiar with the workings of System Monitor. (I'm more of a command-line guy, m'self. :) )

With a lot of utilities that show system-wide RAM usage, the number that is displayed as "free memory" is often alarmingly low. However, this is because of a feature in Linux's memory management procedure.

RAM is ~100 times faster than your hard drive -- for that reason, it is always desirable to have the information you want stored in RAM. So, in an attempt to be helpful, Linux keeps lots of information that you've needed in the past in RAM as a cache. This memory is not exactly "in use" because it would be overwritten if the space was needed. But it's not exactly "free" either, so it doesn't show up as such. As a result, people will often look at the tiny amount of RAM labeled "free" and blame Linux for being inefficient with its memory, when in reality it's quite the opposite.

When you run 'free -m', the column marked 'free' on the row marked '-/+ buffers/cache' is the actual number of megabytes of RAM that are available. (Truly free RAM + RAM used as cache.)

In your case, however, it sounds as though this problem might truly be specific to the program you're running. If System Monitor gives per-process information, look and see what it reports Chrome's memory usage as being. (Alternatively, you could run 'top'.) If it's over a couple hundred megabytes, that's a pretty solid red flag.

The last time I ran "free -m" the amount of free memory was about ~42MB while System Monitor was reporting 95-96% of my memory was being used by the system.

---

### Post by martini1179 on 2010-05-10
> **zaphod777 said:**
> are you running the dev version of Chrome of the beta?

Yes. :) 

I've had this problem with Chrome Beta, Chrome Dev, and Chromium, and it started right around the time that Chrom/ium v5 was released.

---

### Post by martini1179 on 2010-05-11
/bump

---

### Post by martini1179 on 2010-05-12
/bump

---

### Post by martini1179 on 2010-05-15
/bump

---

### Post by c-shadow on 2010-05-22
Use chrome built in task manager (shift+esc). It lists memory usage for the main browser process, all tabs and extensions. Try to see where the memory leaks, it should be one of the three. 
I had similar problems and found out that way some tabs used too much memory and the culprit was javascript.
Open a tab and task manager, than reload a tab a couple of times, memory usage would go up a couple of MB. On some sites no reload was necessary - I could watch memory getting eaten by that tab at a rate of 1 MB/minute!
 Flashblock and adblock extensions were always installed so flash was not a problem. Then i remembered noscript extension in mozilla firefox, disabled all javascript (Options-->Under The Hood-->Content Settings-->Javascript) and later enabled only for a sites where really needed. It seems to be working ok now, memory usage is still high but some leaks are plugged now :)
This thread was helpful:
[http://code.google.com/p/chromium/issues/detail?id=12120](http://code.google.com/p/chromium/issues/detail?id=12120)
There is a link to some crunchgear site in post#22, it's wrapped but here it is if you want to try:
[http://www.crunchgear.com/2009/07/14/blockbuster-ondemand-coming-to-samsung-hdtvs-blu-ray-players-and-home-theater-systems/?awesm=tcrn.ch_5pB&utm_campaign=techcrunch&utm_content=techcrunch-autopost&utm_medium=tcrn.ch-twitter&utm_source=direct-tcrn.ch](http://www.crunchgear.com/2009/07/14/blockbuster-ondemand-coming-to-samsung-hdtvs-blu-ray-players-and-home-theater-systems/?awesm=tcrn.ch_5pB&utm_campaign=techcrunch&utm_content=techcrunch-autopost&utm_medium=tcrn.ch-twitter&utm_source=direct-tcrn.ch)
Default (javascript on), after tab with that page loaded would use 30 MB, after 5 minutes 34 MB and so on...with javascript turned off it would open with 12MB and stay there.

---

### Post by jeneverboy on 2011-12-20
I searched for this problem and found this tread.

When I open about:memory in chromium I see that whenever a silverlight Plug-in is opened the memory usage is building up. With CPU load of 100%.

Closing the tab will not help. Killing the process in the terminal does help.

---

