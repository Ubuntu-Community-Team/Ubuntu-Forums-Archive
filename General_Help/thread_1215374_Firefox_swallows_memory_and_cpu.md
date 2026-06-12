---
title: "Firefox swallows memory and cpu"
date: 2009-07-17
forum: General Help
---

### Post by orrie on 2009-07-17
I am running fluxbox in an regular Ubuntu-install, and the Firefox is lagging after a while.. Very annoying.


*Here are the top when Firefox not running:*
```

top - 09:14:42 up  1:18,  2 users,  load average: 0.50, 0.64, 0.64
Tasks:  91 total,   1 running,  90 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  0.0%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026220k total,   398372k used,   627848k free,    65412k buffers
Swap:  3903752k total,      124k used,  3903628k free,   213424k cached

orrie@xx:~$ uptime
 09:14:48 up  1:18,  2 users,  load average: 0.46, 0.63, 0.63

```
*.. quite normal really.*


*And this under load with Firefox running:*
```

top - 09:04:42 up  1:08,  2 users,  load average: 1.03, 0.93, 0.64
Tasks:  92 total,   3 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s): 62.1%us,  3.0%sy,  0.0%ni, 34.6%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1026220k total,   949496k used,    76724k free,    64224k buffers
Swap:  3903752k total,        0k used,  3903752k free,   231680k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3334 orrie     20   0  676m 549m  28m R 48.8 54.8  19:51.39 firefox    
 2789 root      20   0  170m  33m 7024 S 11.6  3.4   3:05.43 Xorg   
 5178 orrie     20   0 33320  14m 9.9m R  4.3  1.4   0:00.96 gnome-terminal  

orrie@xx:~$ uptime
 09:14:04 up  1:17,  2 users,  load average: 0.43, 0.65, 0.64

```
[I].. and here we can see that Firefox is using 48.8% CPU and 54.8% MEM.
Something isn't right.[/I]


*GFX-card from /etc/X11/xorg.conf:*
```

.....
Section "Device"
 Identifier  "Card0"
 Driver      "radeon"
 VendorName  "ATI"
 BoardName   "Radeon 9200"
 BusID       "PCI:1:0:0"
 Option      "BusType" "PCI"
EndSection

```



I have an suspision that Firefox using a lot of memory when the browser has been idling for some hours, **or** when have runned or running flash-element (YouTube).

It couldn't be the driver I presume?
Have just installed the package xserver-xorg-video-ati.


How to fix this really annoying thing?

---

### Post by lovinglinux on 2009-07-17
> **orrie said:**
> I have an suspision that Firefox using a lot of memory when the browser has been idling for some hours, **or** when have runned or running flash-element (YouTube).

I believe you are correct. High CPU usage could also be due to javascript pages. 

Excessive memory usage could be due to an extension leaking memory.

I recommend following the tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). There are several tips there on how to improve Firefox performance.

I also recommend trying Firefox 3.5. The tutorial also explains how to install it, along with Firefox 3.0

---

### Post by orrie on 2009-07-18
So the problem could not be related to the graphic-driver right?

---

### Post by LightningCrash on 2009-07-18
> **orrie said:**
> So the problem could not be related to the graphic-driver right?

Shouldn't be graphics drivers. You'd see high memory and CPU usage from Xorg if that were the case.

---

### Post by ubuntuben on 2009-07-19
I've also been experiencing the same type of problem lately with Firefox. It's eating up much more RAM than before to the point where the swap memory is being used. This really slows things down to a crawl! Been wondering if there is a memory leak somewhere due to Firefox running. On quitting Firefox, everything goes back to normal. So the temporary solution is to quit Firefox and relaunch it. This has prompted me to buy more RAM to beef up my systems and hopefully avoid using swap memory. The same problem plagues my two desktops running Ubuntu 8.04.2.

---

### Post by orrie on 2009-07-19
I should mention that on my amd64 I haven't got any problems at all.
Just on my laptop that is i386.

Perhaps it's some errors on the 32-bits version?


I'm running Jaunty btw :P



> **lovinglinux said:**
> I recommend following the tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).
[QUOTE=Firefox optimaztion and troubleshooting thread]First make sure you have the proprietary graphics card driver installed. Go to "System >> Administration >> Hardware Drivers" and enable the corresponding driver.[/QUOTE]
I've just done that, and it says "No proprietary drivers are in use on this system.".



Am now trying out Firefox-3.5 to see if I get the same lag.

---

### Post by orrie on 2009-07-20
Now, the big moment is here.
I have installed Firefox 3.5 and been trying it for like 5 minutes.

Right after logging in to Facebook and scrolling down to read an status, then the Firefox have crashed each time.
```

orrie@ubuntu:~$ firefox-3.5 http://www.facebook.com
Segmentation fault

```

Now I'm getting more and more annoyed.
Have been following the guide for optimizing and done this in Firefox 3.0, and now I've been trying 3.5 that are crashing RIGHT after I'm logging into Facebook.

What should the solution be?



**Edit:**
My conky says that Firefox is using 40% CPU and Xorg like.. 14% CPU or so.
Having two tabs up; this URL and playing an YouTube-video.
It's just the CPU that it troubles with, not the memory.
Running it in Firefox 3.0.10.

It shouldn't be like this?

---

### Post by lovinglinux on 2009-07-20
> **orrie said:**
> I've just done that, and it says "No proprietary drivers are in use on this system.".

What about an option to install a driver there?

> **orrie said:**
> Right after logging in to Facebook and scrolling down to read an status, then the Firefox have crashed each time.
```

orrie@ubuntu:~$ firefox-3.5 http://www.facebook.com
Segmentation fault

```

Now I'm getting more and more annoyed.
Have been following the guide for optimizing and done this in Firefox 3.0, and now I've been trying 3.5 that are crashing RIGHT after I'm logging into Facebook.

What should the solution be?

There are some reports of problems with Facebook, but not crashing.

> **orrie said:**
> 
My conky says that Firefox is using 40% CPU and Xorg like.. 14% CPU or so.
Having two tabs up; this URL and playing an YouTube-video.
It's just the CPU that it troubles with, not the memory.
Running it in Firefox 3.0.10.

It shouldn't be like this?

It shouldn't, but it is. I have the same CPU usage when playing flash videos. There is a bug report at [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

---

### Post by orrie on 2009-07-20
> **lovinglinux said:**
> What about an option to install a driver there?
Nop. Nothing at all..


> **lovinglinux said:**
> There are some reports of problems with Facebook, but not crashing.
Mine did crash.

I have now removed ~/.mozilla and restarted the browser.
That did work though.



> **lovinglinux said:**
> It shouldn't, but it is. I have the same CPU usage when playing flash videos. There is a bug report at [http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)
Right now I'm running one pidgin-conversation, gnome-terminal, Spotify through wineserver, and two tabs in Firefox-3.5 (this and addons.mozilla.org).
Xorg and firefox-3.5 are at 3% both now.
It varies a lot though.

Hopefully this should work, but I can't say that for sure further I've tested firefox-3.5 a bit more.


When I'm pressing ALT+TAB it's lagging a little bit, like before.
Really really annoying.

---

### Post by NoBugs! on 2009-07-24
This may help it run faster:
[https://wiki.mozilla.org/JavaScript:TraceMonkey](https://wiki.mozilla.org/JavaScript:TraceMonkey)

---

### Post by running_rabbit07 on 2009-07-24
The only time I ever had a problem with RAM loading up was while in a photo sharing forum, RAM and SWAP filled. Stopped going to that site.

---

### Post by philcamlin on 2009-07-24
java slows my pc down

---

### Post by running_rabbit07 on 2009-07-24
Java speeds me up, lol.

---

### Post by orrie on 2009-07-27
I have reinstalled Ubuntu 9.04 and it did actuallly solve the problem.
Using the standard driver and the screen doesn't lagg that much on Google Apps and Facebook like it did before the reinstall.

Before the reinstall I had 8.04 that have been upgraded to 8.10 and then to 9.04.


Btw..
> **NoBugs! said:**
> This may help it run faster:
[https://wiki.mozilla.org/JavaScript:TraceMonkey](https://wiki.mozilla.org/JavaScript:TraceMonkey)
When clicking on this URL, remove the <b> and </b> and it will work.

---

### Post by NoBugs! on 2009-08-19
> **orrie said:**
> 
This URL returns 404.

That link shouldn't have <b></b>, fix that and it won't show a 404.

I notice that if the "javascript.options.jit.content" and "javascript.options.jit.chrome" are set to "false" in about:config, it seems to fix the Firefox-3.5 slow-loading, freezing, 100% cpu problem.

---

### Post by kerryhall on 2009-09-09
I have this same problem. I load firefox, the only tab open is google.com. BAM, memory usage shoots up to 300 megs virtual, 100 res. This would be laughable, if it weren't so frustrating.

I tried upgrading to swiftfox 3.5 from firefox 3.0.13. Swiftfox is certainly much faster, but still has the same memory problems. Now if I load google.com in lynx, that uses about 7k of memory. Now that is more like it.

Google.com shouldn't cause firefox to use 300 megs within 3 seconds of start up.

---

