---
title: "ubuntu 64bit + firefox + adobe flash + full screen issue"
date: 2010-12-27
forum: General Help
---

### Post by 0949er on 2010-12-27
Hey guys, is there a fix that I am just completely missing that fixes this full-screen bug for flash players? For example, when on youtube, flash works fine, non-buggy, etc. However, If i press fullscreeen, I get basically the same size video (as non-fullscreen) in the middle of my screen, and the rest of the space is just filled with a black background.

Are there any fixes for this? This is pretty much youtube specific, because if I watch other videos on other sites (that use other players?) their full-screen actually works correctly. Any ideas?

---

### Post by 0949er on 2010-12-27
anybody?

---

### Post by efflandt on 2010-12-27
What video card/chip do you have?  Are you using default video drivers or something added with Additional Drivers or some other way?  And are you using flashplugin-installer package or real 64-bit flash from adobe?

I am using nvidia drivers and have never seen that issue.  I just watched a 720p Black Ops youtube video full screen on my 1080p HDTV with real 64-bit flash, and it worked fine.

---

### Post by akand074 on 2010-12-27
I've never seen the problem either. I have the 64 bit flash installed from the Adobe website, with proprietary drivers installed.

---

### Post by lovinglinux on 2010-12-28
I have seen this problem, but I don't remember the exact solution. You could try some things tho.

First, get the latest 64bit square preview. You can easily do that with my extension [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/").

Then apply the tweak for fullscreen issues from [http://www.webgapps.org/flash/issues-and-solutions](http://www.webgapps.org/flash/issues-and-solutions)

If that doesn't work, try to disable effects (Compiz) and see if the problem persists.

---

### Post by 0949er on 2010-12-28
Hey guys, yes I am using the 64bit flash plugin available from adobe flash.

I am also using the proprietary nvidia drivers.

Flash-Aid does not fix my full-screen issue. It is still not going "all the way full screen". Its not choppy though; plays fine. Just not "full screen"

any other ideas?

here is what I mean:
[IMG]http://img264.imageshack.us/img264/4413/screenshotap.png[/IMG]

---

### Post by lovinglinux on 2010-12-28
Create a new Firefox profile for testing and check if the problem persists.

---

### Post by 0949er on 2010-12-28
> **lovinglinux said:**
> Create a new Firefox profile for testing and check if the problem persists.

I logged out and logged onto a different user and I have the same issue. (only this users also has no sound, but I am not worried about why, it is a preliminary account)

---

### Post by lovinglinux on 2010-12-29
> **0949er said:**
> I logged out and logged onto a different user and I have the same issue. (only this users also has no sound, but I am not worried about why, it is a preliminary account)

Then I guess the problem is something related to the video driver. Are you using dual monitors?

---

### Post by lovinglinux on 2010-12-29
Try this: [http://ubuntuforums.org/showpost.php?p=3907569&postcount=2](http://ubuntuforums.org/showpost.php?p=3907569&postcount=2)

---

### Post by 0949er on 2010-12-29
> **lovinglinux said:**
> Try this: [http://ubuntuforums.org/showpost.php?p=3907569&postcount=2](http://ubuntuforums.org/showpost.php?p=3907569&postcount=2)


hey man I appreciate the effort.

FlashAID effectively removed my current working flash player, so I had go and fix that back to normal.

The second option, "Advanced Desktop Options" I found a program in the repository called "CompizConfig settings manager", is that the same program he speaks of? Once installed I found the general tap, as well as the "full screen" box he wants me to uncheck (which it already is unchecked) and I cannot find the "plug-in" area he is talking about.

---

### Post by lovinglinux on 2010-12-29
> **0949er said:**
> hey man I appreciate the effort.

FlashAID effectively removed my current working flash player, so I had go and fix that back to normal.

The second option, "Advanced Desktop Options" I found a program in the repository called "CompizConfig settings manager", is that the same program he speaks of? Once installed I found the general tap, as well as the "full screen" box he wants me to uncheck (which it already is unchecked) and I cannot find the "plug-in" area he is talking about.

Yes, CompizConfig is the Compiz settings manager. 

I haven't used Compiz for a long time, but I guess there is a search function there. Just type Workaround in the search field and it should display the available plugin.

---

### Post by burton247 on 2010-12-29
I have the same issue as this. Well I think so, some large flash games are a bit dodgey. Almost like double buffering isn't enabled. 

But when I'm full screen videos it doesn't work for the web, I have dual monitors and I think the video will only go as large as the smaller monitor. I use metacity and still have the issue

---

### Post by ipwtech on 2011-01-02
It sounds like you have the same problem as me. I have not found a solution yet but if I do ill post it here. If anyone else knows of a solution that would help. My specs are below...

# Specs
Ubuntu 10.10 x64
FireFox & Chrome
Flash 10.1r
Compiz Fusion  +addons
Dual Monitors
using Nvida Drivers most recent

# Video
[http://dl.dropbox.com/u/375995/youtube-full.ogv](http://dl.dropbox.com/u/375995/youtube-full.ogv)

---

### Post by jotie on 2011-03-06
Anyone have a fix for this?

I'm having the same problem. Some of the Flash videos would do fullscreen just fine. Hulu and vimeo work fine with fullscreen but youtube fullscreen is messed up.

Now, if I turn one screen off, fullscreen works perfectly.

I have 10.04 x64
Newest Flash 64 bit from adobe labs
Compiz
NVidia GTS 250
Dual monitor (28" and 17")

---

### Post by TheConsaw on 2011-03-12
> **lovinglinux said:**
>  You can easily do that with my extension [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/").



sir, you are a legend !

---

### Post by lovinglinux on 2011-03-12
> **TheConsaw said:**
> sir, you are a legend !

:-)

I have just released version 2.0.5 with some improvements. Is only available from the extension web site, since I am experiencing issues uploading to Mozilla.

---

