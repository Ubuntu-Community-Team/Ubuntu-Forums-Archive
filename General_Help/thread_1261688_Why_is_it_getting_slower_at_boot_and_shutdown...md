---
title: "Why is it getting slower at boot and shutdown..?"
date: 2009-09-09
forum: General Help
---

### Post by Thanh-BKK on 2009-09-09
Hi.

So i installed Jaunty from scratch a couple of weeks ago and was like "wow is that thing FAST!" - 35 seconds for a full boot (power button to AWN loaded) and a flat EIGHT seconds to shut down.

Those figures were unchanged after i was done with customizing the UI and installing/configuring applications.

But now, two weeks later, it is MUCH slower... and i want to know why that happens.

Boot now takes little over a minute, shutdown some 25 seconds.

This is STILL seriously fast compared to Windows or Hardy, but still it is a lot slower than it WAS. 

And just today i have installed Jaunty on a second computer, installed exactly the same applications and packages (AptOnCD!), tweaked and customized the desktop etc in EXACTLY the same way (same theme, same icon theme, same codecs etc, really like a 1:1 clone) and this freshly installed computer blows the first one out of the water - despite it being a single-core Athlon 64-3000+ while the first is a dual-core Athlon 64 x2-5000+! Now this "slow" machine boots in like 40 seconds and shuts down in 10. Both of them have 2 GB of RAM and identical Nvidia graphic cards with identical drivers. 

What causes Jaunty's slowdown in just two weeks, can it be reversed/"fixed" at all and if so, how? And how can it be prevented from happening again? 

No updates have been installed as the system functions flawless and i don't want new bugs being introduced by updates, updating is disabled. 

Appreciate any advice... many thanks in advance.

Kind regards.....

Thanh

---

### Post by P4man on 2009-09-09
interesting. I noticed a similar behaviour, though not nearly as extreme, and I continually installed and updated stuff, so I blamed that.

Try charting your boot times with this:
[http://webupd8.blogspot.com/2009/04/ubuntu-boot-chart-make-graph-with-your.html](http://webupd8.blogspot.com/2009/04/ubuntu-boot-chart-make-graph-with-your.html)

---

### Post by scouser73 on 2009-09-09
Let me refer you to [[COLOR="Red"]**This Post**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491") which is an excellent tip for getting a much better boot time, although the post is dated 2005 it's still relevant.

I would also like to mention that you disable some start-up programs that you don't use which also has an affect on your boot times.

I would also suggest that you install Bootchart from synaptic Package Manager, search for and install: **Bootchart** & **Pybootchartgui**.  This program shows the user how long it takes for boot times and you can spot any potential bottle-necks.

Here is an image of my boot time to show you what the end result can look like; [[IMG]http://img178.imageshack.us/img178/9270/desktopjaunty200909091.th.png[/IMG]](http://img178.imageshack.us/i/desktopjaunty200909091.png/)

---

### Post by Thanh-BKK on 2009-09-09
Hi.

Ok done that - now i got one of those images as well, i will attach it here. But to be honest i do not know what to make of it.... maybe you could explain to me what it is that gobbles up my time? 

Also, this mentions "34 seconds". I don't know from when to when it measures, what i measure is from the moment i push the power button to the moment AWN appears. That used to be 35 seconds and is now 62. 

What has gotten longer is the time that the system just gives a black screen with a mouse pointer, i.e. after the splash screen and before the desktop appears. 

Oh, and i already disabled unnecessary services via the "Services" application. My machine has a Bluetooth dongle and i use it so that needs to be active. 

Kind regards....

Thanh

---

