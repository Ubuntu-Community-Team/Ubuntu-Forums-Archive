---
title: "Lucid Lynx - Google Chrome (as well as Chromium) causes computer to freeze"
date: 2010-05-03
forum: General Help
---

### Post by JoelJohnson on 2010-05-03
I've been searching around for this on Google but I can't find anything. I've also checked the Chrome bug reports and can't find anything that's the same problem I'm having.

Google Chrome is causing my computer to crash (everything including mouse freezes and caps-lock flashes).

I installed a fresh install of **Karmic** a few weeks back. I installed Google Chrome using the deb from Google's main Chrome page. I upgraded to **Lucid** the night after it was released. It ran fine for a while. The night after I upgraded I had my first crash.  I restarted my computer, restored my tabs in chrome, browsed for only a minute before the same thing happened. This time I didn't restore my tabs in Chrome. After a few minutes of browsing the same thing happened. I used Firefox and didn't have a problem. I opened Chrome and within seconds it crashed. I have yet to have this problem without Chrome being opened.

I completely removed Chrome (apt-get purge and removed the ppa from my sources). Reinstalled it - same problem. I removed it again and tried Chromium, same problem. I installed Chromium with the dev channel. Same problem.

I've talked to several people who are using Lynx and don't have this problem. I tried running Chrome from the terminal to see if it would dump anything before the crash, but it doesn't.

Since I just installed fresh just a few weeks ago, it wouldn't be that difficult to do a fresh install, but I really would prefer not to as I'm in the middle of a semester at school and I use my computer heavily. I suppose it's not the end of the world to have to use Firefox, but I really prefer Chrome.

I was hoping someone here could help me out. Maybe help me find some kind of log to figure out what's causing this. Should I file a bug report?

Just a side note: I never had a crash using Karmic.

I have a Lenovo Thinkpad T61p. Running the 64bit version of Ubuntu (gnome) Lucid Lynx.
If you need any more details let me know. I can easily reproduce this problem.

Thanks for the help.

---

### Post by JimTaverna on 2010-05-03
It's been stable, very stable, for me under both Karmic and Lucid, especially compared to the random Flash crashes I experienced under Windows. Unlike you though I did a clean install of Lucid.

Frankly, I've been using the Dev versions for a while now and have never had it lock up my laptop. Might crash the browser, but for the most part, the sandbox approach works well and I usually just lose the tab.

Best way is to either use the Page Icon>Developer>Developer Tools or Javascript Console and step through the code, if you can.

In addition, enable (I thought it was on by default in Beta/Dev Builds) logging and see if you can catch what's faulting.

Here's a link:

[http://www.chromium.org/for-testers/enable-logging](http://www.chromium.org/for-testers/enable-logging)

Good luck...

---

### Post by skiver on 2010-05-03
The crashing of Chromium-browser just happened to me after upgrade from karmic to lucid.
I had an entry in /etc/apt/sources.list.dchrome.list.distUpgrade and karmic version of chromium-browser was installed. After removing all source lists for chromium I reinstalled the proper version. Now its working fine

---

### Post by 98cwitr on 2010-05-03
download the .deb straight from Google after removal. If your trying to install from repo you're repo might be fubar'd. I'm running Chrome fine...I just had to put my damn icon back after installing 10.04...it's like the upgrade reset my gnome-desktop

---

### Post by dilaudid on 2010-05-03
This looks like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871) - bug affecting chrome users running lucid on thinkpads. Does ```
lsmod | grep ath
``` show the module ath5k?

---

### Post by DomesDKG on 2010-05-03
I'm using chrome on a thinkpad and haven't had any problems, but I installed it through the ubuntu software center, maybe this has something to do with it?

---

### Post by dimeotane on 2010-05-03
I'm running Karmic, and Chromium was running perfect up until I did an updated this afternoon, now it's freezing constantly.  Its so unuseable I'm back into firefox. 
 This seems related.

---

### Post by moldovan_catalin on 2010-05-04
Same situation here, after upgrade to 10.04 after starting Google Chrome it doesn't take more than a couple of minutes and the system hangs and is unusable until reboot. Doesn't seem though to happen with Firefox.

---

### Post by scouser73 on 2010-05-04
> **98cwitr said:**
> download the .deb straight from Google after removal. If your trying to install from repo you're repo might be fubar'd. I'm running Chrome fine...I just had to put my damn icon back after installing 10.04...it's like the upgrade reset my gnome-desktop

+1 for this advice.

---

### Post by curvelot13 on 2010-05-04
I am having the same problem on a MacBook 1,1.  I did a fresh install of Lucid Lynx and downloaded the .deb directly from google.  It worked fine for the past few days, but today it started crashing every few minutes.

---

### Post by martinpm24 on 2010-05-04
My problem not freeze the machine, freeze with some page but only the browser. All it came after the last update.

---

### Post by yamagami on 2010-05-04
I have a similar problem on my Thinkpad T61p, and although Chrome has been open and running each time htis happened, I think the problem relates to audio/video playback. 
When I played some flash movie clip, and later when I played some mp3 in Totem, I had the same crash - the computer completely hangs, the caps lock light flashes and the last bit of audio plays in a wierd loop. A this stage, no button combination other than holding down the power button will get me anywhere and the mouse is not responding. 

Harel

---

### Post by mgiammarco on 2010-05-05
I have thinkpad r50p and after installing lucid I have several hard crashes on each day!!

I am using firefox and not chrome.

I suspect they are related to:

1) ath5k chipset OR
2) video driver (interaction with chrome and/or firefox)

So basically lucid with any THINKPAD is not stable!

---

### Post by davidj411 on 2010-05-08
I am using a Lenovo R61 and since i upgraded my version of ubuntu to Lucid Lynx, google chrome (beta version) has crashed every time i use it. machine locks up until reboot. i removed chrome and am using another browser until a new version of chrome comes out.

---

### Post by mgiammarco on 2010-05-10
> **mgiammarco said:**
> I have thinkpad r50p and after installing lucid I have several hard crashes on each day!!

I am using firefox and not chrome.

I suspect they are related to:

1) ath5k chipset OR
2) video driver (interaction with chrome and/or firefox)

So basically lucid with any THINKPAD is not stable!

I add new report: 

- my home workstation radeon based now crashes too with ubuntu 10.04 and it has radeon chipset (and no wifi)
- my laptop crashed again with firefox and this time connected to wired ethernet.

I have two crashes a day: fifteen years ago I have started using linux because windows was crash prone. Now ubuntu made this possible also to linux: thank you!

---

### Post by JanHJT on 2010-05-10
> **JoelJohnson said:**
> Google Chrome is causing my computer to crash (everything including mouse freezes and caps-lock flashes).

Exactly what happend to me with Chrome beta straight from Google on a Thinkpad R51 with lucid 32-bit. I'm using chrome right now without a crash:

reboot
remove /home/user/.config/Google and .../google-chrome
restart chrome
do _not_ sync your bookmarks (Set Up Sync...)!

That's it. I don't know why, but it's working

---

### Post by curvelot13 on 2010-05-15
Just turning off Bookmark Sync fixed it for me.

---

### Post by mgiammarco on 2010-05-17
> **mgiammarco said:**
> I add new report: 

- my home workstation radeon based now crashes too with ubuntu 10.04 and it has radeon chipset (and no wifi)
- my laptop crashed again with firefox and this time connected to wired ethernet.

I have two crashes a day: fifteen years ago I have started using linux because windows was crash prone. Now ubuntu made this possible also to linux: thank you!

I solved myself the problem. I have installed kernel 2.6.34rc7 and now works perfectly. It is incredible that a vanilla RC kernel works better than the official "stable" ubuntu kernel!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by gnumbo on 2010-05-20
Hi, I am having similar issues. How did you go about installing kernel 2.6.34rc7?

---

### Post by radi8 on 2010-05-22
Install Kernel Kernel 2.6.32-4 rc7. This will solve the problem.

---

### Post by StuartN on 2010-05-22
> **gnumbo said:**
> Hi, I am having similar issues. How did you go about installing kernel 2.6.34rc7?

The Ubuntu-specific instructions are very straightforward: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds), and you probably want kernel 2.6.34-lucid if you are updating Ubuntu 10.04 Lucid: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

---

### Post by jbird80 on 2010-06-02
> **curvelot13 said:**
> Just turning off Bookmark Sync fixed it for me.

Same here, turning off browser sync worked for me. every once and a while i'll turn it back on and restart chrome to sync my bookmarks. I then turn sync back off.

---

### Post by xslick on 2010-06-08
Turning off syncing worked for me too

---

### Post by viordiasko on 2010-06-09
I wasn't using Chrome but my new pc (lucid 64bit) was constantly crashing. Anywhere from 1-60 mins after boot up.

I thought it was dodgy RAM or motherboard settings so I tried a lot of variations. I did note a ath5k warning being echoed to standard out so I removed the wi-fi card, et voila, stability!

So I googled, found this topic & upgraded the kernel as per [[COLOR="Blue"]Stuart N's post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9341612&postcount=21") #21 & now I have wi-fi networking. The downside being I lost my fglrx for the onboard ATI card...until I added the [xswat ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/"), installed fglrx & amdccle via Synaptic,  rebooted, & reactivated compiz via the "Visual Effects" tab in System>Preferences>Appearance.

---

