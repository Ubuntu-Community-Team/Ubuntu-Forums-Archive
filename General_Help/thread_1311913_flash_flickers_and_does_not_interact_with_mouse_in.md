---
title: "flash flickers and does not interact with mouse in firefox"
date: 2009-11-02
forum: General Help
---

### Post by simon303 on 2009-11-02
I have just upgraded to 9.10 via Update-Manager. When I try to use flash in firefox it flickers alot and when I try to click on anything it has no response.

I have tried reinstalling flashplugins-nonfree and flashplugins-installer but to no avail. When I try to use firefox's "Install missing plugin" option it can't find the files on the net.

I the 64bit version installed, which I know sometimes means things aren't available, but it claims all the flash stuff is available.

Does anyone have any suggestions??

Simon

---

### Post by sschafer on 2009-11-04
I have a similar problem.  Flash will either not respond to any mouse clicks or will respond to one and then ignores any subsequent clicks.  I have an amd 64 and upgraded to ubuntu 9.10 yesterday.  Firefox was upgraded to 3.5 and had flash 10.0.32.18 installed.  In an attempt to fix it I downloaded 10.0.32.18 64 bit flash directly from adobe and copied libflashplayer.so to /usr/lib/mozilla/plugins but that just caused firefox to crash.

---

### Post by flipper9 on 2009-11-04
You are running the 32-bit version of the flash plugin which is causing the problems.  A workaround is to right-click on the flash plugin, then left-click off once, then you can click the plugin just once.  Repeat as necessary.

You can also install the alpha-version of the 64-bit version of the adobe flash plugin.  Search the forums for instructions.

---

### Post by bnr on 2009-11-06
I am running the 32 bit version and that workaround has absolutely no effect on my computer.

It seems that everyone is having this problem regardless of graphics hardware, so I suspect that it is more related to the flash plugin then graphics drivers.

The only thing I have found that works is to click through embedded videos and view them at their source.

---

### Post by beubanks on 2009-11-17
I've encountered a similar issue where left-click does not work in Flash.  Is it just left-click that is broken for you all, or is right-click broken too?

The following bug report by someone else describes my issue exactly.  I also am getting the  problem in both Eclipse (Java IDE) and Flash:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/452938](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/452938)

The workaround here fixed my problem in Flash but not in Eclipse:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

Note: I did not encounter the flickering problem.

---

### Post by Deathspawn on 2009-11-27
Same problem here also. Happens a lot when trying to play this: [http://ninjakiwi.com/Games/Tower-Defense/Play/Bloons-Tower-Defense-4.html](http://ninjakiwi.com/Games/Tower-Defense/Play/Bloons-Tower-Defense-4.html)

Like, get to the difficulty selection and if it happens to you, you will get it. And no, before you go thinking it is just that game, it happens with a lot of other stuff that it used to never happen with. Even Youtube Videos. Tried upgrading and the workaround and even tried to install a nonfree flash and nothing worked.

**Edit: **Flash seems to work fine in Opera.

---

### Post by Anagonda on 2009-11-30
> **Deathspawn said:**
> Same problem here also. Happens a lot when trying to play this: [http://ninjakiwi.com/Games/Tower-Defense/Play/Bloons-Tower-Defense-4.html](http://ninjakiwi.com/Games/Tower-Defense/Play/Bloons-Tower-Defense-4.html)

Like, get to the difficulty selection and if it happens to you, you will get it. And no, before you go thinking it is just that game, it happens with a lot of other stuff that it used to never happen with. Even Youtube Videos. Tried upgrading and the workaround and even tried to install a nonfree flash and nothing worked.

**Edit: **Flash seems to work fine in Opera.

Yeah, few days ago I wanted to play bloons 4 but no go. It flickers like hell and after a while it just freezes.

I have noticed that every web page that has flash on it uses alot of cpu power.
Now if I open Bloons 4 game my other cpu load goes to 90+% and the other is in between 70-100%. So flash slows whole computer.

If I open like ten youtube videos each in its own tab, but I watch only one, my firefox will freeze totally. Only way to get out of it is to go to terminal and kill firefox. Some times my firefox freezes so bad that it takes over 10 minutes to open terminal.

---

