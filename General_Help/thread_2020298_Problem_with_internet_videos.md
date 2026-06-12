---
title: "Problem with internet videos"
date: 2012-07-08
forum: General Help
---

### Post by ubigix on 2012-07-08
Hi,
I have Ubuntu 11.04 with Firefox 13.0.1.
I'm not able to watch videos from Internet (YouTube, news site, ecc...).
I have installed all the flash plugins, I'm able download the video, but I'm not able to watch them.
I have the same problem also with Chromium, message "Missing Plug-in".
I also tried all the update (Ubuntu, Firefox, Chromium), with no apparent effect.
Do you have any idea about what I can do?
Thanks

p.s.: It's the first time for me in this forum, excuse me if I have posted this thread in the wrong place

---

### Post by kensum on 2012-07-08
We need a little hardware information in order to figure out where the problem could be. In the mean time: did you install -ubuntu restricted extras- which you need. In firefox right click a video window and go to settings and uncheck hardware acceleration. Just a couple of things to try until we know where the problem is for sure. good luck.:)

---

### Post by ubigix on 2012-07-12
Here some more information.

About what you suggest, simply nothing happens! Once I have loaded the video page, I have an empty area where the video is supposed to be, and with the right click I don't have any menu.

My laptop is an old Asus Notebook L3000D with AMD Athlon XP-M 2400+ and 512 MB RAM.
From the Firefox Tools/Adds-on menu I have the following plugins  installed and enabled:
1) DivX Web Player 1.4.0.233 (last update 5/19/2010)
2) iTunes Application Detector (last update 6/25/2012)
3) QuickTime Plug-in 7.6.6 (Totem 2.30.2) (last update 5/19/2010)
4) Shockwave Flash 11.2 r202 (last update 5/11/1012)
5) VLC Multimedia Plugin (compatible Totem 2.30.2) (last update 5/19/2010)
6) Windows Media Player Plug-in 10 (last update 5/19/2010)

The following plugin is disbled (it has been suggested by a guy on Internet to solve the problem, but it didn't):
1) Shockwave Flash 9.0 r999 (last update 8/23/2009)

About the extension, aways in the Firefox Tools/Adds-on menu I have the following enabled:
1) Dizionario Italiano 3.3.2 (last update 6/16/2012)
2) Easy YouTube Video Downloader 6.2 (last update 7/8/2012)
3) Firefox Ubuntu Modifications 0.9.5 (last update 5/12/2012)

The Appearance is Default 13.0.1 (last update 7/4/2012)

The funny thing is that, Video Downloader 6.2 works perfectly, I cannot see the youtube videos but I can download them.

Other info: my wife has another Ubuntu Netbook (Asus Eee Pc with Ubuntu 12.04 LTS), and she was able to configure it and now it works good. We tried the same things on my old Asus but they didn't work.

Thanks for your help. Probably you will say "Let's buy a new laptop!", but now is for me a principle battle!

WM

---

### Post by evilsoup on 2012-07-12
I've never needed it, but I've heard good things about the Firefox add-on 'Flash-Aid': this should remove conflicting versions of flash & flash plugins. It might be worth a go.

Another thing that you might find handy, especially for an older system like what you have, is the FlashVideoReplacer add-on - it enables the use of (IIRC) mplayer embedded in your browser rather than a flash add-on to play Youtube videos, and uses less system resources. Unfortunately, it only seems able to play Youtube videos on the website (no embedding), and certain videos don't work, but it is still useful.

---

### Post by ubigix on 2012-07-13
I've tried also this solution (Flash aid), but with no results.
Anyway, thanks
Any other ideas?

---

### Post by Redblade20XX on 2012-07-13
> **ubigix said:**
> I've tried also this solution (Flash aid), but with no results.
Anyway, thanks
Any other ideas?

Hmmm...that's strange. Can you try youtube's html5 support to see if your laptop will play any video? It may point to a gpu problem.

[http://www.youtube.com/html5](http://www.youtube.com/html5)

- Red

---

### Post by GreatDanton on 2012-07-13
I had the exact same problem on different laptop (also 512mb ram). Like you mentioned before (go buy new laptop), that is the only solution for you. I was trying for almost one week and I was not able to watch videos properly. The best result I got was with html5. If that doesn't work for you, then I am afraid you will not be able to watch videos properly. Flash player is not very well suported in Linux and that's the issue.

Good luck!

---

### Post by GreatDanton on 2012-07-13
Take a look at that link: [http://ubuntuforums.org/showthread.php?t=1942988](http://ubuntuforums.org/showthread.php?t=1942988)

There I said the problem is solved, but after 1 day I realized that actually is not solved, lol. Maybe it will help you, maybe it will not. Try it and tell us.

Regards.

---

### Post by Autodave on 2012-07-13
[QUOTE=ubigix;12085176]Hi,
I have Ubuntu 11.04 with Firefox 13.0.1.
I'm not able to watch videos from Internet (YouTube, news site, ecc...).
I have installed all the flash plugins, I'm able download the video, but I'm not able to watch them.
I have the same problem also with Chromium, message "Missing Plug-in".
I also tried all the update (Ubuntu, Firefox, Chromium), with no apparent effect.
Do you have any idea about what I can do?
Thanks

No guarantte here, but my ASUS runs fine by eliminating flash altogether and installing GNASH from the software center.

---

### Post by ubigix on 2012-07-19
I tried with GNASH, but I after the installation by the software center I don't find it.
Where is it supposed to be? As a plugin in Firefox or as a independent software?
Anyway, I tried again with youtube, and other news websites as well, with no results:(
Thanks

---

