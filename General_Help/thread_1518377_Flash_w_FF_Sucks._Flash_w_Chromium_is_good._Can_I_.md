---
title: "Flash w/ FF Sucks. Flash w/ Chromium is good. Can I even the field?"
date: 2010-06-26
forum: General Help
---

### Post by Roasted on 2010-06-26
Flash with Firefox: Full screening videos is a joke since it'll go full screen, yet half of the video is off of the screen. I also cannot click on certain videos, such as YouTube's older design of flash videos. I cannot exit the ads, mute, fast forward, etc. 

Flash with Chromium: I can full screen without issue. I can mute, fast forward, etc without issue. Everything works with Chromium.

But, I like Firefox. Is there anything I can do with Firefox?

---

### Post by cj.surrusco on 2010-06-26
Pick your fate. It's the Yin and Yang of web browsing.

---

### Post by Roasted on 2010-06-26
> **cj.surrusco said:**
> Pick your fate. It's the Yin and Yang of web browsing.

Sorry - I don't see that as a feasible answer. Some people are delighted with Flash working in Firefox. I want to know how.

---

### Post by cj.surrusco on 2010-06-26
Well, to watch youtube in fullscreen with firefox, I let the video buffer then use Ubuntu's movie player to watch the flash video that is downloaded to the /tmp folder.

---

### Post by XSAlliN on 2010-06-26
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line:

export GDK_NATIVE_WINDOWS=1

Before this line:

. /usr/lib/nspluginwrapper/noarch/npviewer

Example:

> #!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer

---

### Post by cj.surrusco on 2010-06-26
> **XSAlliN said:**
> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Add this line:

export GDK_NATIVE_WINDOWS=1

Before this line:

. /usr/lib/nspluginwrapper/noarch/npviewer


This never worked for me, it's probably only a fix for 32 bit, correct?

---

### Post by philinux on 2010-06-26
> **cj.surrusco said:**
> This never worked for me, it's probably only a fix for 32 bit, correct?

You should not be using the 64 bit plugin at the moment due the well published security flaw.

The above is a fix for using the 32 bit plugin on a 64 bit install. And for 32 bit installs.

---

### Post by XSAlliN on 2010-06-26
No, as far as I know this is a linux 64 bit problem on linux 32 bit should run fine (I'm on Ubuntu 64bit).

Maybe you got it wrong (it doesn't work if you misspelled something). Try edit again, remove all content from the original file, copy paste the quoted content:

> #!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer

...and it should work (this is what fix it for me). 

=====

**[Here's a list of other tweak]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")**s but the above one should fix the full-screen problem.

> **philinux said:**
> You should not be using the 64 bit plugin at the moment due the well published security flaw.

The above is a fix for using the 32 bit plugin on a 64 bit install. And for 32 bit installs.

I thought he was using that, 64 bit plugin is just bad... looked promising when released, but not worth mentioning any-more. Adobe also drooped the support on it.

---

### Post by cj.surrusco on 2010-06-26
I am using the 32bit plugin with 64bit Ubuntu. But the fix still doesn't work for me. Maybe it has something to do with the fact that I am running multiple monitors?

---

### Post by XSAlliN on 2010-06-26
You could also try to **[install it with this add-on]("https://addons.mozilla.org/en-US/firefox/addon/161939/")** - once you add it to firefox, you'll see the icon on right corner, down... 

It will clean the other alternatives that could conflict and install the right version for you. Maybe it helps... was made just for that.

---

### Post by philinux on 2010-06-26
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Roasted on 2010-06-26
> **philinux said:**
> [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

Yeah that... did nothing. :(

---

### Post by cj.surrusco on 2010-06-26
> **Roasted said:**
> Yeah that... did nothing. :(

Didn't work for me either, unfortunately.

---

### Post by Roasted on 2010-06-28
Can anybody confirm that they indeed have Firefox working 100% with flash with no issues whatsoever? Every box I install Ubuntu on, regardless of hardware, I have issues... Losing hope with Firefox's reliability to be an all-around browser. Sure, it may not be Firefox's fault, but if it doesn't work -everywhere- how is it a viable browser to use?

---

### Post by XSAlliN on 2010-06-29
There's not 1 software (from any distribution), that I could say it runs 100% flawless, even if it kinda does. In my case, Flash runs pretty decent with FF - yet far from perfect, not even the browser is in that position. My main problems with flash, is related to "occasionally not showing content on YouTube (unless I restart the browser) or Righ-Click-ing in some flash games freezing FF (in this situation killing the browser is the only say to go).

Yet Chrome, is far from beeing a better alternative then FF... Yes, it was optimized to give a better performance - but that's the only decent feature it has... being simply AWFUL IN TERMS of SECURITY. 

If security is not a priority for you, if marketing ads don't bother you, if extensions compatibility is not important for you then yeah - for a use like this Chrome could be the best browser... 

I did use Chromium "JUST FOR YouTube" - until version 3.6.4 where they fixed some problems related to video streaming.

---

### Post by Roasted on 2010-06-29
> **XSAlliN said:**
> There's not 1 software (from any distribution), that I could say it runs 100% flawless, even if it kinda does. In my case, Flash runs pretty decent with FF - yet far from perfect, not even the browser is in that position. My main problems with flash, is related to "occasionally not showing content on YouTube (unless I restart the browser) or Righ-Click-ing in some flash games freezing FF (in this situation killing the browser is the only say to go).

Yet Chrome, is far from beeing a better alternative then FF... Yes, it was optimized to give a better performance - but that's the only decent feature it has... being simply AWFUL IN TERMS of SECURITY. 

If security is not a priority for you, if marketing ads don't bother you, if extensions compatibility is not important for you then yeah - for a use like this Chrome could be the best browser... 

I did use Chromium "JUST FOR YouTube" - until version 3.6.4 where they fixed some problems related to video streaming.

Can you elaborate on how Chrome is bad at security? I heard the opposite, and that it rivals the security levels of Firefox...

---

### Post by Don Barzini on 2010-06-29
> **Roasted said:**
> Can anybody confirm that they indeed have Firefox working 100% with flash with no issues whatsoever? Every box I install Ubuntu on, regardless of hardware, I have issues... Losing hope with Firefox's reliability to be an all-around browser. Sure, it may not be Firefox's fault, but if it doesn't work -everywhere- how is it a viable browser to use?

I'm running 10.04 64-bit and haven't run across any real problems with Flash. At least no problems that haven't always existed with Flash.

I didn't install Flash from the Ubuntu repositories. I did on one install and it really wasn't acceptable (much higher CPU utilization). I downloaded the 64-bit version from Adobe.

Now, it's not Flash 10.1 which was pulled by Adobe. It's Flash version 10.0.45.2. It works fine for me. Your mileage may vary.

You can dowmload the file here.....

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Extract the plugin to **.mozilla/plugins** in your home directory. You will probably need to create the **plugins** directory. It is not there by default.

You will also first have to remove the Flash you installed from the repositories before installing and using this Flash plugin.

---

### Post by Don Barzini on 2010-06-29
Also....

Some of you might consider upgrading your version of Firefox.

The latest and greatest as of today is version 3.6.6

To do so.... in a terminal type...

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
```

Then run...

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by XSAlliN on 2010-06-30
> **Don Barzini said:**
> I'm running 10.04 64-bit and haven't run across any real problems with Flash. At least no problems that haven't always existed with Flash.

I didn't install Flash from the Ubuntu repositories. I did on one install and it really wasn't acceptable (much higher CPU utilization). I downloaded the 64-bit version from Adobe.

Now, it's not Flash 10.1 which was pulled by Adobe. It's Flash version 10.0.45.2. It works fine for me. Your mileage may vary.

You can dowmload the file here.....

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Extract the plugin to **.mozilla/plugins** in your home directory. You will probably need to create the **plugins** directory. It is not there by default.

You will also first have to remove the Flash you installed from the repositories before installing and using this Flash plugin.

That version of Flash has "holes in it" and they also dropped support for 64 bit version of flash. With few tweaks here and there flash 32 bit runs better... 

> **Roasted said:**
> Can you elaborate on how Chrome is bad at security? I heard the opposite, and that it rivals the security levels of Firefox...

Did mentioned this several times, so I'll just quote myself for this answer:

> **XSAlliN said:**
> It all depends on what you want from a browser, cause the speed of chrome comes with a price:

As far as I'm concern, Chrome is the spy-ware browser...

But not a spy-ware for a specific type of users, but one for a major company like Google. Which means, you don't have to worry about Credit Card frauds or something like that... There's an old saying: "information is power" - Google being the biggest marketing corporation on the Internet has a very good use for this power. So, they won't harm users in any way, that would be against their "current" interests... They just want to gather data regarding users interests.

As you all know by now, at current times Internet is the best place for that:

-you want to buy something, you browse the Internet
-you're interested in some future gadgets, you browse the Internet
-you're looking for a specific product (from any domain) you browse the Internet
-you're looking for a specific place for a vacation, you browse the Internet.
... and so on.

Until Chrome was released, their search engine (Google) and their mail client (Gmail) was a very good tool for that, yet with Google Chrome they have even more control which obviously, can lead to more accurate results. This will increase their profits significantly, as mentioned above - without hurting those involved.

It's all up to you as user, if you agree with that or not... which is obviously coved by their EULA Yet, I strongly believe 99.9% of all Goggle Chrome users never looked at it (same as they proceed with any EULA).

========

I use Firefox for general usage, yet I also have Chromium installed for YouTube - since under Linux 64 bit flash doesn't work as wanted under Firefox, yet works pretty decent under Chromium. YouTube is also part of Google, so it makes no difference. And yes, I one of those rare people that don't accept their entire policy and also read EULA's. 


...some of it is just ethics related, **[but this is something I won't accept]("http://forums.informaction.com/viewtopic.php?f=10&t=1676")**, yet I'm aware it's in Google's interest "to be non-functional". They're already loosing milions of $ with Firefox cause of Adblock and NoScript and only around 30% of FF users have this add-ons installed...

At current time is doesn't have the hardware acceleration of Chrome, but as a browser is fast enough and as far as I know "the most secure browser"... So, that's something worth considering... at least from my point of view.

It rivals FF only in terms of performance, not security... Yet I guess, it could rival Internet Explorer 5.0/6.0 but that on Windows. :)

---

### Post by spacearena on 2010-08-31
Chromium is faster at loading, but my experience so far is "crash", "crash", "browser disappeared", "extension crashed", "where did my flash video go???????? oh yeh it's behind the browser??????"

I wouldn't say Chromium is better than firefox at all my experience has been poor. Yes, firefox crashes, but not 20 times a day. I've rarely had a problem with flash in firefox in the last 2 years, but I'm having issues in Chromium.

---

### Post by sticky_icky on 2010-10-28
**I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  **I HAVE THE SOLUTION** for this problem, for everybody that has flash issues, _when all embedded flash goes fullscreen on every site except youtube or googevideos_.  

      I wish to christ i could have found this years ago...  i have the  same  problem, main monitor is 1440x900, running an xfx geforce 7600gt,  and  everything but youtube works.  flash/youtube/ubuntu=HUGE #$^@##@   headaches for years.  i tried litterally hundreds of workarounds or   fixes, HOURS of time trying to get the stupid flash fixed for more than 2   minutes, and not one single thing worked, ever, until now.t

      ubuntu forums had been completely useless to me, in those  endeavors,  wasted much time for nothing, though, in fairness to the  buntu, i fully  acknowledge the fruitful efforts of the ubuntu team, the  linux world has  made HUGE strides forward since i started with  slackware7.   with  ubuntu, the reality is that aside from arbitrary  reference, i haven't  needed the forums, everything but flash, some  really obscure software,  works like a charm, since the nvidia driver  issues have been  sorted.(btw, for me, the only way to install properly  working nvidia  drivers/nvidia settings/flashplugin is with apt from  terminal after  stopping gnome...**not with synaptic from the desktop**)

     since nothing's ever worked for me, i didn't bother reading the  thread, i'd be shocked if it was mentioned... anyway, after a routine  cleaning/reinstallation of firefox i happened across this:[ http://www.addonfox.com/]("http://www.addonfox.com/"),   which icludes some really good addons for firefox....also some bs, the   converter, swifclick, and windowshopper addons pissed me off...

the real gem of that collection, which i had never found before is:

**[flashvideoreplacer 1.0.5]("https://addons.mozilla.org/en-US/firefox/addon/161869/")**

      it "replaces embedded flash videos with quicktime or windows media   player compatible videos."   WHAT THAT MEANS IS IT COMPLETELY REPLACES   THE WHOLE, STUPID, YOUTUBE/GOOGLEVIDEO GUI AND **EMBEDS IN ITS PLACE MPLAYER**.
(in the preferences,the selection for plugin/mimeType, is "windows media player (application/x-mplayer2)

hall-o-fu#%ing-luja!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

     _**this is the only thing that has ever worked for me**_,   and it seems to be a really solid addon, so far as i can tell, not   buggy, video looks great-not choppy, options exist to automatically   choose the quality of youtube videos, choose cache size(default is   2megs), enable post processing, all the gnome mplayer interface   settings, etc.  _it doesn't seem to change anything on any video sites except youtube/googlevideos, and optionally vimeo and blip.tv etc._  only problem is i haven't been able to get the youtube playlist to autoplay the next vid.

if  you are frustrated wit yt/google, try this.  i can confir, it works   with gnome mplayer on 10.04.1 LTS.  i have every video and audio   application i could find, though, not sure of the impact other packages   have on mplayer/vice-versa.
[B]
hope this works for you, NO need to thank me if it does, but--

         PLEASE[/B] **PLEASE PLEASE help others when you have solutions.**

god bless.

---

