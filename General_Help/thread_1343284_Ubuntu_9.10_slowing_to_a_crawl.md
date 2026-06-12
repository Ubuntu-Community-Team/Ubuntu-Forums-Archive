---
title: "Ubuntu 9.10 slowing to a crawl"
date: 2009-12-01
forum: General Help
---

### Post by slasc on 2009-12-01
I recently upgraded my home media/email server from Ubuntu 9.04 to Ubuntu 9.10.  I was previously having no problems with my machine at all.  However, after upgrading to 9.10, I am experiencing a severe performance degradation after a couple of days.  I have scoured the logs as best I can, and found nothing that explains it.  At first, it was coming to a complete stop.  I could flip on the monitor and even the clock was standing still.  Now though, it's coming to an extreme crawl.  I get timeout errors when trying to ssh into it, and VNC takes about 10 minutes just to transmit the background.  This is not normal behavior for this machine.  Since I use this machine as an IMAP server for my primary email, this means that I find myself suddenly unable to access my email.  Furthermore, I have to be physically near the machine to reboot it, usually with the reset or power button.

Does anyone have any idea what's going on or how I can track this down?  I'm leaving town soon, and I can't have people going over to my place every 48 hours just to reboot a computer.

Someone, please help!!!

(I would include detailed system specs, but I don't have them on my at the moment.  I know it's an x86_64 install on an Athlon CPU (I believe it's only single core, but it might be dual..)  It's got an NvVidia card inside.  I believe it's a GeForce 8000 series.  That's about all I remember at the moment, and I'm not physically near the machine, so I can't easily look it up)

Thank you!

---

### Post by slasc on 2009-12-01
I could really use some help in tracking this down.  It gets so laggy that, when logging in, connections are established and sometimes authenticated, but never completed.

By the way, if you have a Windows 7 machine that maps drives to a Ubuntu 9.10 machine (like I do) and your Ubuntu 9.10 machine is going super laggy (like mine does after a day or two), Windows 7 will not let you login.  It hangs and mimics the appearance of the dreaded Black Screen of Death.  Thankfully, rebooting my Ubuntu 9.10 machine relieved my Windows 7 machine's login woes.

I could very much use some help in figuring out how to find out what's wrong with my Ubuntu 9.10 machine.  I would really prefer not to reinstall...

---

### Post by slasc on 2009-12-02
I looked up my system info in the profiler, and this is what I am running (in case that helps)

-Computer-
Processor		: AMD Athlon(tm) 64 Processor 3200+
Memory		: 1023MB 
Operating System		: Ubuntu 9.10
-Display-
Resolution		: 1024x768 pixels
OpenGL Renderer		: GeForce FX 5200/AGP/SSE2
Audio Adapter		: Audigy - SB Audigy 1 [SB0090]
-Printers (CUPS)-
SCX-4500_Series
Stylus-CX5000

---

### Post by ed-koala on 2009-12-02
Open a terminal on the machine and type

```
top
```

See what's using up all your cpu/memory.

---

### Post by slasc on 2009-12-04
> **ed-koala said:**
> Open a terminal on the machine and type

```
top
```

See what's using up all your cpu/memory.

Unfortunately, when this is happening, I can not access the OS in any useful way.  I need some way of logging my performance.  Perhaps a way to output the top command's data to a logfile, activated by a cron job???  I'm not really sure how to do that...

---

### Post by hwttdz on 2009-12-04
When you login you could start a 
top -b -dX > my_top_log.txt
where X is the number of seconds between top grabs, then wait until it locks up then later on look at the file.

---

