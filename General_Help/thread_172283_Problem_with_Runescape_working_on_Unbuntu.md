---
title: "Problem with Runescape working on Unbuntu"
date: 2006-05-08
forum: General Help
---

### Post by captain_bogus on 2006-05-08
Hi,

I'm so close to having Ubuntu working perfectly for me.  FYI, Runescape is a MMORPG that runs in a web browser under Java.  I can get Java installed just fine, but after a few seconds of playing, Firefox will either crash or freeze up.  This is bad because I'm addicted to Runescape.

I have a Toshiba Satellite L25-S1192 and a ATI RADEON XPRESS 200M.

After installation X windows will not come up.  To get into X I have to log in to the cli and use VIM to change my /etc/X11/xorg.conf video device from "ati" to"vesa" and reboot.  Only then with X come up.

I have installed Sun Java as directed by the Wiki:

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restricted%29#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

I even tried upgrading to Firefox 1.5.

I tried a totally clean install by deleting my Ubuntu partition and reinstalling and only adding Java.  But that didn't work either.

I'm thinking it could be my video driver?  Any ideas?

Any help getting Runescape running for me would be greatly appreciated.

--bog

---

### Post by kroiz on 2006-05-09
I have firefox 1.5 and java 1.5 and rune scape works for me, except that its loading time is much slower then on windows. and some times when the free servers are busy it does not load at all.
I have radeon 9000 mobility.
I would guess too that it is your video driver, but then again I what do I know!
threre is an howto on how to install the latest ati driver maybe you should try that.
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

### Post by captain_bogus on 2006-05-10
Yes, I installed the driver as directed in the link you gave me.  It works now.

It does lag a lot though.  I can play in windows just fine, but in Linux it's not so great.  I wish I knew enough to make it play as well as it does in windows.  I'd be willing to bet if there was a client that played Runescape outside of the browser, like Swiftswitch ([http://www.swiftswitch.net/](http://www.swiftswitch.net/)) that it would perform a lot better

--bog

---

### Post by kroiz on 2006-05-11
[quote=captain_bogus]I'd be willing to bet if there was a client that played Runescape outside of the browser, like Swiftswitch ([http://www.swiftswitch.net/]("http://www.swiftswitch.net/")) that it would perform a lot better

--bog[/quote]

I dont think so because I tried running runscanpe in other browser and it performed the same, maybe the java implementation for linux is to blame.

---

### Post by TonyB0312 on 2006-07-26
Most of the Runescape-Linux threads I have seen seem to all point to what you already know, it has it's issues. And in regards to Swiftswitch, it will probably never make it out of the Windows world. VB doesn't emulate well, if at all. 

I've placed some questions in the creator of Swiftswitch (strider3282), so hopefully I will have some more info on it later on.

Best of luck

---

### Post by Want A Pie on 2007-12-14
I can't get runescape to work either... I'm using gutsy, so that link above didn't help

---

