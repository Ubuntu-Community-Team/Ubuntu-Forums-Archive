---
title: "Lubuntu web browsing experience"
date: 2012-04-27
forum: General Help
---

### Post by oslub on 2012-04-27
Hello. I have an old desktop on which I installed Lubuntu 11.10, yesterday I upgraded to 12.04. This desktop has just 1GB of RAM. 

I know I could just buy some more RAM or even a new motherboard but the times are tough and I really need to save money to apply on something lighter than my almost 3kg Toshiba laptop to carry to the University, such as an ultrabook or tablet, so I need to make the most of this old computer for basic usage. That is why I installed Lubuntu in dual boot with windows xp.

In general, after more than a month of usage, I can't say I am unhappy with it, it runs smoothly in most cases and fits my basic needs and it really is lightweight as I wanted.

While running applications, using LibreOffice, transfering files and navigate on folders is faster than Windows XP, browsing the web is getting each time slower, worse than what happens on XP and it gets worse everytime a new flash version is available.

It's pratically impossible to use my Firefox with my usual add-ons and even with Chromium with no add-ons, I can't have more than 2 or 3 simple tabs opened (news portal for example) without the system freezing almost completely. The interesting thing is that when I run the command "free -m", most of the times there is more than half memory free.

Do you have any ideas on why web browsing is so slow on Lubuntu? Why doesn't it use the free RAM (sometimes up to 600/700MB free to use)? How can I improve this situation?

Thank you very much in advance.

---

### Post by marinara on 2012-04-27
The RAM situation sounds normal, Linux likes to use lots of RAM to make a memory cache.

Can you give more details about the freezing during browsing the web?  Is it only on flash-intensive websites?
Are any other applications slow to launch?

---

### Post by Vaphell on 2012-04-27
run top/htop in terminal and see the numbers during the page load.
do you cut down the amount of crap running on webpages, like tons of flash ads and 3rd party scripts with adblock/noscript?
flash is a resource hog, there is no other way to call it. If your machine is old, flash and a lot of javascript could make it grind to a halt. What are your comp's specs?
Sometimes problem with gfx drivers can cause excessive freezing, everything is ok with it?

---

### Post by oslub on 2012-04-28
> **marinara said:**
> The RAM situation sounds normal, Linux likes to use lots of RAM to make a memory cache.

Can you give more details about the freezing during browsing the web?  Is it only on flash-intensive websites?
Are any other applications slow to launch?

I think that flash websites make it worse yes, videos on youtube lag very much for example but it is not exclusive of them.
Also, loading new pages and webpages elements takes as much time as using a  slow internet connection, not instantaneously as we are used to with  latest versions of Chrome and Firefox.

I want to make clear that the Lubuntu system itself is not slow, just the navigation on web pages is, which is the reason why I started this thread,

Taking as example Windows XP, which I run in dual-boot with Lubuntu, indeed it is getting nearly impossible to watch videos, specially with good quality, after the recent releases of flash plugin. However, webpages load instantaneously and when I open too much tabs or run more than two or three applications at same time, the entire system freezes as whole (browsers, windows explorer and opened apps).

On Lubuntu it is different, right now I am having what I consider an already very acceptable usage of this  computer: on desktop 1 Mozilla Firefox with 5 tabs, this forum, hotmail,  google reader, editing a text document on google drive and facebook. On desktop 2 I have abiword, pidgin, gimp and playing a video on GNOME  Player, and on tray keepass and dropbox. There are still over 500MB of  RAM free, several apps in use and still the system is running fast, which is what I love about  Lubuntu.

The problem is really about navigating the web... scrolling a document on google docs takes forever, as I said, new pages take a lot to load, everything is pretty much lagging and sometimes even switching tabs is very slow, but the Lubuntu itself runs fine, I can use all other opened applications without delays.

So there seems to be some incompatibility of my lubuntu with internet pages, flash is certainly a main responsible, but I would like to know if there is something I can do to have a better experience browsing in lubuntu (I already accepted the fact that I need to download a video or open it on a standalone player to watch it smoothly on this computer lol).

About other applications slow to lauch, there is the particular case of keepass, on windows it takes about 10-15 seconds to open the database but on lubuntu and also on ubuntu it takes close to 5 minutes!!

---

### Post by oslub on 2012-04-28
> **Vaphell said:**
> run top/htop in terminal and see the numbers during the page load.
do you cut down the amount of crap running on webpages, like tons of flash ads and 3rd party scripts with adblock/noscript?
flash is a resource hog, there is no other way to call it. If your machine is old, flash and a lot of javascript could make it grind to a halt. What are your comp's specs?
Sometimes problem with gfx drivers can cause excessive freezing, everything is ok with it?

Yes I agree with you about flash and in my opinion is getting worse at each update, I am getting more and more difficulties watching videos and playing flash games on this desktop, no matter what OS I use.

Here are some specs, Intel Pentium 4E, 2800 MHz (5.25 x 533), 1014 MB  (DDR SDRAM), Graphic adapter Intel(R) 82865G Graphics Controller  (96 MB), motherboard P4i65G.

I will try adblock and noscript, I'm sure it will be helpful. Thanks for the tip.

---

### Post by claracc on 2012-04-29
I have a pentium III laptop with 512 Mb ram and 64 Mb for sys 630/730 graphics card running lubuntu 11.10.

The two last flasplayer plugins don't work with web browsers firefox or chromium in this laptop, I had to do the downgrade step of flash in order to watch flash videos.

Here, you have a thread explaining what you can do in order to workaround: [http://ubuntuforums.org/showthread.php?t=1953796&highlight=flash+lovinglinux](http://ubuntuforums.org/showthread.php?t=1953796&highlight=flash+lovinglinux)

Anyway, my laptop is lower resources than yours and flash videos are played in low motion, not linux fault but adobe flash. As it can be said you always can use flashvideo replacer addon in firefox to watch some flash videos in mp4 format.

---

### Post by Rodney9 on 2012-04-29
Try Low Quality Flash

and

Flash Aid Plugins 

Rodney

---

### Post by oslub on 2012-04-29
> **claracc said:**
> I have a pentium III laptop with 512 Mb ram and 64 Mb for sys 630/730 graphics card running lubuntu 11.10.

The two last flasplayer plugins don't work with web browsers firefox or chromium in this laptop, I had to do the downgrade step of flash in order to watch flash videos.

Here, you have a thread explaining what you can do in order to workaround: [http://ubuntuforums.org/showthread.php?t=1953796&highlight=flash+lovinglinux](http://ubuntuforums.org/showthread.php?t=1953796&highlight=flash+lovinglinux)

Anyway, my laptop is lower resources than yours and flash videos are played in low motion, not linux fault but adobe flash. As it can be said you always can use flashvideo replacer addon in firefox to watch some flash videos in mp4 format.

Thank you for that thread, I will try the solutions given by lovinglinux. It is a post which adresses exactly my problems with videos and webpages in general.

---

### Post by oslub on 2012-04-29
> **Rodney9 said:**
> Try Low Quality Flash

and

Flash Aid Plugins 

Rodney

I will, thank you for the tip ;)

---

### Post by oslub on 2012-04-29
claracc posted the thread adressing this issue, so I will mark this thread as solved, anyone who has the same problem please visit:
[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796).

---

