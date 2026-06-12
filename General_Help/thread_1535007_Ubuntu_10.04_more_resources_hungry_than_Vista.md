---
title: "Ubuntu 10.04 more resources hungry than Vista ?"
date: 2010-07-20
forum: General Help
---

### Post by zer2 on 2010-07-20
Hello to all

I was lately wondering whether ubuntu 10.04 consumes more of CPU compared to vista ?

I did a small test if i can call it that way. Anyway, I used vista and I was surfing the net (i used Opera browser) When I checked Vista's Task manager > performance it showed 1-4 percent of cpu usage.

I did the same thing with ubuntu 10.04. i also used opera to surf the net. When I checked system monitor it showed CPU1 - 24% CPU2- 10%

Now I don't get this. i always thought and was told that linux is really not resources hungry OS. Now I don't know what to think.

I have 1GB RAM , core 2 duo E6750 2,66Ghz, Palit GeForce 7600GS 256MB DDR2/128bit TV/DVI PCI-Express, MSI P31 Neo - F V2 motherboard

---

### Post by philinux on 2010-07-20
> **zer2 said:**
> Hello to all

I was lately wondering whether ubuntu 10.04 consumes more of CPU compared to vista ?

I did a small test if i can call it that way. Anyway, I used vista and I was surfing the net (i used Opera browser) When I checked Vista's Task manager > performance it showed 1-4 percent of cpu usage.

I did the same thing with ubuntu 10.04. i also used opera to surf the net. When I checked system monitor it showed CPU1 - 24% CPU2- 10%

Now I don't get this. i always thought and was told that linux is really not resources hungry OS. Now I don't know what to think.

I have 1GB RAM , core 2 duo E6750 2,66Ghz, Palit GeForce 7600GS 256MB DDR2/128bit TV/DVI PCI-Express, MSI P31 Neo - F V2

Unfortunately System Monitor is resource hungry. Try using the command top in a terminal.

---

### Post by zer2 on 2010-07-20
I checked it and what do you think 

[IMG]http://i28.tinypic.com/316r96e.png[/IMG]

This one's when I'm hcecking film on Youtube

[[IMG]http://img16.imageshack.us/img16/4254/screenshot1rx.png[/IMG]](http://img16.imageshack.us/i/screenshot1rx.png/)


this one is from Vista's task manager
[[IMG]http://img715.imageshack.us/img715/8066/screenshot2qt.png[/IMG]](http://img715.imageshack.us/i/screenshot2qt.png/)

**I need your help, is there any way to make it more CPU friendly ?**

---

### Post by zer2 on 2010-07-21
Anyone there ?

---

### Post by snowpine on 2010-07-21
You are using less than half of your CPU resources while watching Flash video (a very CPU intensive activity). So long as your computer is performing acceptably I see nothing wrong here.

If you are experiencing performance issues watching videos, then a good place to start is by making sure you're using the correct video drivers (if applicable).

To answer your larger question, Windows Vista and Ubuntu 10.04 have identical CPU and RAM requirements; I am not sure where you got the "less resource hungry" idea but it is not accurate in my opinion and experience.

>  If you want to run Windows Vista on your PC, here's what it takes:

    * 1 gigahertz (GHz) 32-bit (x86) or 64-bit (x64) processor
    * 1 gigabyte (GB) of system memory (512 megabytes (MB) for Home Basic)
    * 40 GB hard drive with at least 15 GB of available space (20 GB for Home Basic)
    * Support for DirectX 9 graphics with WDDM and 128 MB of graphics memory (32 MB for Home Basic)
    * DVD-ROM drive
    * Audio Output
    * Internet access (fees may apply)

> Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

---

### Post by moore.bryan on 2010-07-21
It's not about "resource hungry," but about resource management. Don't just fire-up Opera on one machine and another to compare; rather, open thirty applications on both and see which one handles their respective resources better.

---

### Post by Vaphell on 2010-07-21
30% cpu while running flash videos is peanuts
also remember that due to marketshare much more effort went to optimize windows versions of commercial software.

---

### Post by RJARRRPCGP on 2010-07-21
Ubuntu, IIRC don't even require 512 MB of RAM.

---

### Post by zer2 on 2010-07-21
Don't get me wrong i don't say quality sux ubuntu is very fast in my case.

but in vista in task manager when I start it   shows 1-3 , 1-4 percent cpu usage. In ubuntu on the other hand I get 3-7 right away. Also I hear that muy PC is louder then i use ubuntu , I'm wondering is something wrong with nvidia divers and ubuntu synchronization. Here's what I get when I run opera 

[[IMG]http://img291.imageshack.us/img291/7650/screenshotfk.png[/IMG]](http://img291.imageshack.us/i/screenshotfk.png/)

---

### Post by snowpine on 2010-07-21
> **zer2 said:**
> Don't get me wrong i don't say quality sux ubuntu is very fast in my case.

but in vista in task manager when I start it   shows 1-3 , 1-4 percent cpu usage. In ubuntu on the other hand I get 3-7 right away. Also I hear that muy PC is louder then i use ubuntu , I'm wondering is something wrong with nvidia divers and ubuntu synchronization. Here's what I get when I run opera 

[[IMG]http://img291.imageshack.us/img291/7650/screenshotfk.png[/IMG]](http://img291.imageshack.us/i/screenshotfk.png/)

You are comparing apples and oranges. If Vista is fast, and Ubuntu is fast, then who cares if one uses slightly more CPU than the other? The odds they would use *exactly* the same amount of CPU are very small, right?

That being said, if you have nvidia, you absolutely need to install the correct driver for optimum performance. I am not an nvidia user personally, so I will let other users chime in. Here is the wiki page to get you started: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by cliffdodger on 2010-07-21
> **Vaphell said:**
> 30% cpu while running flash videos is peanuts
also remember that due to marketshare much more effort went to optimize windows versions of commercial software.

I have to jump in here and second this point. Adobe isn't going to spend as much time optimization their flash player plugins for Linux when as a desktop it only has what, around a 5% market share? (forgive me if I'm wrong). Compare that with the time they would spend making sure their windows flash plugins works great since windows probably has around an 80-90% desktop market share. Their main audience is windows. If flash is taking up more cpu on windows than on linux it's not because linux is "slow" it's because Flash hasn't optimized their application very well to run on Linux. They could probably achieve comparably lower cpu usage on Linux with more time and development. A lot of enterprises don't take their Linux app versions as seriously as their windows versions - skype anyone?

---

### Post by zer2 on 2010-07-26
well thanks guys for the info.

 I'm just wondering if that constant higher CPU usage doesn't shorten life of that CPU. What do you think ?

ALSO I'm wondering how much more electricity will PC use ?

---

### Post by cliffdodger on 2010-08-04
Constant peak cpu shouldn't affect overall cpu life "much" if you have good cooling - I would think. Can't say for sure. That's more of a question for someone at a site like tomshardware (I may be wrong)

You'll use more electricity cooling your over active cpu then your cpu will probably use doing the processing.

---

