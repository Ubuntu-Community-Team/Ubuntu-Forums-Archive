---
title: "Ram Usage"
date: 2010-05-31
forum: General Help
---

### Post by jaco223 on 2010-05-31
Since the final release of Lucid, why is it consuming more RAM than the Beta
or RC? I checked with the command line free- m and it say I have on 77 megs
of ram free..I'm only running firefox 3 tabs open. Is there a memory leak
happening...I'm running kernel 2.6.32-22 generic. Seems to me with beta
on boot it was only using around 179 megs of ram.....
Any help or insight is greatly appreciated

Jaco

---

### Post by Serpher on 2010-05-31
Webpages can consume a lot of RAM. Without any other information such as how much RAM you have, we can't really do much troubleshooting however.

---

### Post by lovinglinux on 2010-06-01
Reboot, start Firefox in safe mode or create a new profile without extensions and browse for a while to see if there is any difference. 

Although memory leaks occur in the browser itself, extensions are good candidates for culprits. For example I have fixed a memory leak on one of my experimental extensions a couple of weeks ago.

If you open links on new windows instead of tabs you can boost the memory leak, since some extensions load javascripts whenever a new window is opened. If this extension has a leak, then it will increase memory usage really fast. In this case, it doesn't matter how many tabs you have open.

That doesn't mean you shouldn't use extensions. I have more than 50 installed and Firefox runs pretty well. You just need to keep your eyes open when you install new extensions and update those already installed.

---

### Post by jaco223 on 2010-06-01
> **lovinglinux said:**
> Reboot, start Firefox in safe mode or create a new profile without extensions and browse for a while to see if there is any difference. 

Although memory leaks occur in the browser itself, extensions are good candidates for culprits. For example I have fixed a memory leak on one of my experimental extensions a couple of weeks ago.

If you open links on new windows instead of tabs you can boost the memory leak, since some extensions load javascripts whenever a new window is opened. If this extension has a leak, then it will increase memory usage really fast. In this case, it doesn't matter how many tabs you have open.

That doesn't mean you shouldn't use extensions. I have more than 50 installed and Firefox runs pretty well. You just need to keep your eyes open when you install new extensions and update those already installed.

Guys
Thanks for the replies. Here's what I have going on. I have only 1GB  of RAM (sad I know) I run firefox as opposed to Chrome or Chromium they seem to be resource hogs
even  with two or three extensions, and open tabs suck RAM too, my other issue with those two browsers the fonts have  blue hinting to them which I can't figure out to save my life, I have an iMac from 2008 which isn't really a shoddy built in LCD panel display.
Anyway here's the extensions I have running with Firefox:
bit.ly sidebar
Hootlet
Press this (from wordpress)
These reside in the toolbar
Extensions :
Shorten URL
Stumbleon
Ubuntu Firefox Modifications
Zementa
AdBlock+
Alexa toolbar
Bindwood
Echofon
Fkickr original
Grease monkey
Hootsuite
Page speed
Prism
Rescue Time
Rescue time firefox extension
I know maybe that extension overload, perhaps you could suggest which ones I kick to the curb so to speak. I blog at wordpress.COM and some of the extensions were installed as a way to get to Twitter, Alexa, and Stumbleon

Any more advice is greatly appreciated.
Jaco

---

### Post by lavinog on 2010-06-01
I am noticing a memory leak also.  I started noticing it last night, but I haven't narrowed it down yet.  It does seem to creep up faster when I use chromium.  I have system monitor tray on the panel.

---

### Post by lovinglinux on 2010-06-01
> **jaco223 said:**
> Guys
Thanks for the replies. Here's what I have going on. I have only 1GB  of RAM (sad I know) I run firefox as opposed to Chrome or Chromium they seem to be resource hogs
even  with two or three extensions, and open tabs suck RAM too, my other issue with those two browsers the fonts have  blue hinting to them which I can't figure out to save my life, I have an iMac from 2008 which isn't really a shoddy built in LCD panel display.
Anyway here's the extensions I have running with Firefox:
bit.ly sidebar
Hootlet
Press this (from wordpress)
These reside in the toolbar
Extensions :
Shorten URL
Stumbleon
Ubuntu Firefox Modifications
Zementa
AdBlock+
Alexa toolbar
Bindwood
Echofon
Fkickr original
Grease monkey
Hootsuite
Page speed
Prism
Rescue Time
Rescue time firefox extension
I know maybe that extension overload, perhaps you could suggest which ones I kick to the curb so to speak. I blog at wordpress.COM and some of the extensions were installed as a way to get to Twitter, Alexa, and Stumbleon

Any more advice is greatly appreciated.
Jaco


For the font issue see the last item on this [list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html). For the extension memory leak, you will have to disable all of them and test one by one. See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

There is also [an extension to test for memory leaks](https://addons.mozilla.org/en-US/firefox/addon/2490/).

---

### Post by lavinog on 2010-06-01
I wrote a script to log memory usage each minute while starting and stopping xclock between intervals.
This is what I got so far:
[img]http://ubuntuforums.org/attachment.php?attachmentid=159067&stc=1&d=1275433039[/img]
I had some issues oocalc so I used gnumeric to plot the graph.  I couldn't figure out how to label the x-axis which is in minutes.
used mem is used memory reported by the free command
and rss is a sum of rss reported by ps -eo rss

I am suspecting fglrx or something related to the gem leak reported during the beta.
glxinfo reports glx version 1.4

---

### Post by jaco223 on 2010-06-01
The font issue is with chrome and chromium not FF .....

Jaco

---

### Post by jbrefort on 2010-06-02
> **lavinog said:**
> 
I had some issues oocalc so I used gnumeric to plot the graph.  I couldn't figure out how to label the x-axis which is in minutes.

Just add a label to the axis (I know, off topic).

---

### Post by dino99 on 2010-06-02
have had memory leak with generic kernel but not with pae kernel

---

### Post by Gimmie5Bukks on 2010-06-02
Same problem for me .I share the same firefox profile with both Windows & Ubuntu.When in Ubuntu the process uses min. 150mb of ram with even 1 tab and can go over 400mb after a copuple of ours of browsing.I windows it rarely goes over 150mb.Same thing with vuze (azureus).With the same torrents on Ubuntu runs using over 300mb increasing Xorg as well over 300 at the same time,while on win vuze barely goes over 100mb.
I also tried a new ff profile,barely a difference.

I have 3gb ram with ubuntu amd64 also the kernel 2.6.32.22

---

### Post by lavinog on 2010-06-02
With desktop effects disabled (and ubuntuone,) memory usage seems to stay constant.  I am going to try testing again with desktop effects enabled to see if the memory leak returns.

To OP: try disabling desktop effects.

edit: found a bug report that might explain my issue, (just need to wait for the memory get used up to test it):
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)
The bug report has a small mention about a memory leak with fglrx and compiz...the solution is to run glxinfo to reclaim the memory.

---

### Post by Rubi1200 on 2010-06-02
I have not experienced the same issues as the OP. However, turning off Desktop Effects significantly reduced memory usage on my laptop from approximately 19-20% of RAM to 10-12%

---

### Post by lavinog on 2010-06-02
This is fglrx with compiz enabled.
```

 free;glxinfo >/dev/null;free
             total       used       free     shared    buffers     cached
Mem:       4056512    1383736    2672776          0      65616     390544
-/+ buffers/cache:     927576    3128936
Swap:      1020088          0    1020088
             total       used       free     shared    buffers     cached
Mem:       4056512    1112844    2943668          0      65616     390544
-/+ buffers/cache:     656684    3399828
Swap:      1020088          0    1020088

```
just running glxinfo freed 270Mb.

Apparently nvidia users are seeing a similar thing too.

---

