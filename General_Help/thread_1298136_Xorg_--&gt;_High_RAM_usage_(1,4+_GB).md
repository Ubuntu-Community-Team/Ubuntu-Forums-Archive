---
title: "Xorg --&gt; High RAM usage (1,4+ GB)"
date: 2009-10-22
forum: General Help
---

### Post by Orian90 on 2009-10-22
Hi all,

For some time now, a program called "Xorg" on ubuntu (9.04) is using more and more memory. After a fresh start up it's about 100 MB, but a few hours later it's more than 1,4 GB. Since I only have 2 GB RAM, this is quite a lot, and often slows my computer down, especially since I'm using The Gimp a lot, which also consumes a lot of memory (which is normal ofcourse).

Does anyone know what the reason is Xorg uses so much memory? I already tried stopping the program by using the system monitor, but it just restarts/does not (don't know, because the computer freezes for about half a minute) itself with the same high memory used.

Anyone who can tell me what it is and what I can do about it?

Thanks in advance

---

### Post by QIII on 2009-10-22
From the wiki world:

The X Window System (commonly X or X11) is a computer software system and network protocol that provides a graphical user interface (GUI) for networked computers, and was initially developed as part of Project Athena. It implements the X display protocol and provides windowing on raster graphics (bitmap) computer displays and manages keyboard and pointing device control functions. In its standard distribution, it is a complete, albeit simple, display and human interface solution, but also delivers a standard toolkit and protocol stack for building graphical user interfaces on most Unix-like operating systems and OpenVMS, and has been ported to many other contemporary general purpose operating systems. Desktop environments such as OpenWindows, CDE, GNOME, KDE, and Xfce, use the X Window System.

It's probably not a good thing to try to stop it and expect anything but frustrating results if you don't take care and know what you are doing and why.

Some things to look at:

Are you using vino (desktop sharing)?

How much stuff do you have running on your desktop?

What applications are you running?

Are you using xscreensavers or gnome-screensavers?

Do you have an ATI graphics card?  Intel?  nVidia?

Could you go to the terminal and post the results of

```
top
```It may or may not be an issue, depending on conditions.  Remember that *nix systems do not manage memory the same way that Windows does.  "Used" memory does not necessarily mean it can't be "reused".  The OS will dole what is not really being used back out as necessary.

I am not sure if this has been resolved, but there was a regression in a previous version of Xorg that caused actual memory leakage if certain types of graphical items were displayed.

---

### Post by Orian90 on 2009-10-22
First of all: thank you for your help O:)

So if I read the wiki correct, Xorg is the program that displays everything on the screen, a bit like the videocard driver on windows (I only switched a few months ago ;) ).


"Are you using vino (desktop sharing)?"
As far as I know, I do not use this tool, unless it is pre-installed with ubuntu. I never installed/used it myself (and I'm the only user on this pc, so pretty it ain't here if it wasn't installed together with ubuntu)

:?:"How much stuff do you have running on your desktop?"

First of all, it's a laptop, not a desktop (not sure if it will make a difference though). I assume with "desktop" you mean what I have on the taskbar? 
Not really the same things everytime, but often it's Firefox (1 of 2 times), 1 or 2 chat screens from pidgin, and maybe openoffice (texteditor) or Gimp (which often does use a lot of memory after . Nothing really heavy for a pc.

:?: "What applications are you running?"

I don't really know what you mean with this, do you mean everything what you can see when I open the systemmonitor?
It's a lot. However, nothing (besides Xorg) that uses a lot of memory. This is a screenshot of the program's that use the most RAM (Xorg is around 300MB now, because I restarted about 30-40 min ago)
[img]http://i35.tinypic.com/2podt1l.png/[/img]
(Sorry about the lay-out, but if I made the screenshot smaller, I was afraid you would not be able to read it)


:?: "Are you using xscreensavers or gnome-screensavers?"

I do use the screensaver that shows flowing Ubuntu signs, but am not sure which one of those it is (could you tell me how I can see this?. Because you said this, I tested it, by letting the screensaver do his work for about a min, Xorg gets around 6MB extra RAM usage, could this be the/one of the cause(s)?

:?:"Do you have an ATI graphics card? Intel? nVidia?"

I have an mobility radeon 2600 (ATI) card. The rest of my pc consists of a dual core T5250 (1,50 Ghz) and 2 gig of RAM.

:?:"Could you go to the terminal and post the results of "top"?"

The result is this:

```
imre@PC-van-Imre:~$ top

top - 21:15:49 up 42 min,  2 users,  load average: 0.43, 0.34, 0.35
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.0%us,  7.2%sy,  0.0%ni, 78.6%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2060728k total,  1119032k used,   941696k free,    66176k buffers
Swap:  3180828k total,        0k used,  3180828k free,   301956k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                   
 6760 imre      20   0 33612  20m  14m S   16  1.0   0:43.97 gnome-system-mo                                                                           
 2970 root      20   0  675m 350m  24m S   13 17.4   4:27.99 Xorg                                                                                      
 6988 imre      20   0 36224  14m 9.8m S    6  0.7   0:00.78 gnome-terminal                                                                            
 3871 imre      20   0  263m 121m  29m S    4  6.0   4:11.04 firefox                                                                                   
 2545 messageb  20   0  3032 1320  772 S    1  0.1   0:04.22 dbus-daemon                                                                               
 3677 imre      20   0 37344  27m 8716 S    1  1.4   0:27.25 compiz.real                                                                               
 3678 imre      20   0 46828  27m  16m S    1  1.4   0:11.56 gnome-panel                                                                               
 3682 imre      20   0 84408  30m  15m S    1  1.5   0:11.18 nautilus                                                                                  
 2709 root      20   0 20108 6312 2016 S    0  0.3   0:06.62 wicd                                                                                      
 3698 imre      20   0 29712  15m 9296 S    0  0.8   0:01.54 wicd-client                                                                               
 7007 imre      20   0  2448 1208  912 R    0  0.1   0:00.07 top                                                                                       
    1 root      20   0  3084 1884  564 S    0  0.1   0:01.49 init                                                                                      
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                  
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                               
    4 root      15  -5     0    0    0 S    0  0.0   0:00.25 ksoftirqd/0                                                                               
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                               
    7 root      15  -5     0    0    0 S    0  0.0   0:00.95 ksoftirqd/1                                                                               
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0                                                                                  
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1                                                                                  
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                   
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0                                                                                   
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1                                                                                   
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                             
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                             
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                 
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                 
   18 root      15  -5     0    0    0 S    0  0.0   0:00.46 kacpid                                                                                    
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                              
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                                                    
   21 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/0                                                                                     
   22 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/1                                                                                     
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                   
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd  
```

---

### Post by QIII on 2009-10-22
There is a reported bug here that talks about slow performance, but does not specify high memory usage:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

One of the people who posted talked about the same GPU as yours.

As I have time, I'll see if I can find more.

Edit:  By the way:  Do you keep FF running a lot?  Does the machine show the same behavior if you don't use FF after starting up and using some of the other applications?

---

### Post by Orian90 on 2009-10-22
Thank you. I also googled and only found things about a high CPU usage, something that does not happen with me though. 

It also happens when I'm not using firefox (not even starting it at all). Often, I just use my computer as music player (banshee). Just starting the computer, turning on some music, and when I take a look at it (sometimes 3 hours later) the RAM usage is very high (at least 1 Gig, often more). While I didn't even touch the pc...

It has neither anything to do with banshee btw, also when I do not use it, the same happens :(

Edit: I checked the website, and indeed, I did have the same problem. However, I fixed it using this patch: [http://ubuntuforums.org/showpost.php?p=7553081&postcount=9](http://ubuntuforums.org/showpost.php?p=7553081&postcount=9) . Now I'm using compiz effects. Could those still be the problem?

---

### Post by XCan on 2009-10-22
For me xorg tend to grow if I run games through Wine. Although the grow is no way near the growth rate you are experiencing. :(

---

### Post by QIII on 2009-10-22
> **Orian90 said:**
> Now I'm using compiz effects. Could those still be the problem?

Only one way to find out ...

---

### Post by Orian90 on 2009-10-23
Well, I tried turning compiz off, but it did not really make a difference. At startup, it does use less memory, but it rises just as fast as when compiz is turned off. However, after this, I turned off my screensaver (just a black screen now), and at the moment it seems to rise slower at least. It hasn't stopped yet, but it definately takes longer :)

---

### Post by QIII on 2009-10-23
Screensavers, even when not active, do take resources.

I haven't dropped this.  I just haven't had time to do more research.

I do know for certain that my machine with an ATI GPU causes Xorg to use significantly more resources than my machines with nVidia (and even Intel!) GPUs.

I think this is a known "issue", but I'm not sure there is a work-around.

---

### Post by Orian90 on 2009-10-23
Thank you :). I'm also continuing my search, and hoping 9.10 may fix it. But unfortunately, till now I can only find things about high CPU usage.

---

