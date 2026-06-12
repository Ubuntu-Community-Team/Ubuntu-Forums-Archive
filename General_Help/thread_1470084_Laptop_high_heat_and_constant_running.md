---
title: "Laptop high heat and constant running"
date: 2010-05-02
forum: General Help
---

### Post by AndyP79 on 2010-05-02
Hi Ya'll,
 Just put a fresh clean copy of Lucid on the laptop. I have noticed this for a while on the otherr versions and distros also, and finally started looking at. My laptop runs, contantly.The fan seems to be always running. I don't have more the a couple of applications at time, I don't use it for work, so nothing extensive. Web browsing, music, email, photos. End user stuff. So I added a heat application in the panel just to see what was happening. I can get the temp down to around 150F-ish if I am not even looking at the laptop. But, open anything and start workingand I am sitting arround 183F-185F. Is this normal? I am just getting toired of having such a hot laptop on my lap, I even have a pad under it so the air can circulate witht the fan, but, a constant running fan is what I have and the heat can be felt through the pad if I am sitting for a couple of hours.

Someone guide me on fixing this please? I am tired of being able to cook eggs on my laptop! LOL!

---

### Post by techunit on 2010-05-02
Did you install the restricted Graphics Driver? Nvidia Graphics Run HOT! It could be that the driver is causing problems. ATIs Drivers Cause the system to run really hot. I removed it and Fans Started running at a good calm speed and I was in business !

---

### Post by mikewhatever on 2010-05-02
Look under System->Admin->System-Monitor, Processes tab. What process consume the most CPU?

---

### Post by shaka_zulu on 2010-05-02
Open terminal and type command: top. Make print screen and put picture here so we can analyze it.

---

### Post by UbuNoob001 on 2010-05-02
Hi there, I too am having this issue, and noted the poster above mentioned the restricted drivers. I downloaded them. Not sure if maybe we have the same problem...Will be following this post.

---

### Post by AndyP79 on 2010-05-02
Okay, i saw one thing was that banshee was running high on the cpu, so I quit that, but it still seems high. Is this normal now? This is what I got from the command top in the termial.



tandy@Lucid64Laptop:~$ top

top - 15:34:25 up  1:51,  2 users,  load average: 0.54, 1.09, 1.15
Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.0%us,  7.3%sy,  0.0%ni, 87.7%id,  3.3%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   1796968k total,  1676024k used,   120944k free,    26984k buffers
Swap:  5261304k total,        0k used,  5261304k free,  1234828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  736 root      20   0     0    0    0 S  6.6  0.0   0:29.33 phy0               
 1026 root      20   0  152m  29m  10m S  1.3  1.7   1:24.79 Xorg               
 6874 andy      20   0  232m  16m  11m S  0.3  0.9   0:02.14 gnome-terminal     
    1 root      20   0 23704 1908 1244 S  0.0  0.1   0:00.43 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.54 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.03 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                 
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default        
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.06 kblockd/0

---

### Post by ZoSo86 on 2010-05-12
Hello, I have a similiar problem.
I have a laptop, model: Compaq CQ61 (google drives me here).
And before Lucid version, in Karmic, when I'd turn on my laptop, cpu's temperature used to be 27ºC (81ºF) and doing a normal use, the temperature used to be around 40ºC (104ºF).
Now in Lucid version, I just turned on my laptop and the temperature is 43ºC (109ºF) and I guess that in a few minutes will be around 60ºC (140ºF).
The others temperatures (GPU and HDD) are normal, as before Lucid.
And this happens in 32 and 64 bits version. I think that the problem is in the kernel, but I tried solve it with the 2.6.34-rc7 one ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/)) and the issuse keeps on.
Help us please, we don't want a stove with wifi in summer!!
Some idea???
Thanks

---

### Post by reloweb on 2010-05-29
I have the same problem.
I use a NVIDIA 7300GT card with proprietary drivers (version 256.25)

---

### Post by chrisinspace on 2010-05-29
This is happening to me as well.  Last night it actually got so hot watching a DVD, it totally crapped out.  I tried to restart and I couldn't even see the POST.  I thought the card was fried, but it worked again after cooling overnight.  Nvidia GeForce 7800 series using the latest proprietary drivers.

---

### Post by reloweb on 2010-05-30
Somebody could open a new bug in launchpad?

---

### Post by chrisinspace on 2010-05-31
I changed the nVidia driver from "NVIDIA accelerated graphics driver (version current)" to "NVIDIA accelerated graphics driver (version 173)" and it seems better now.  I'm not sure if it was just the act of reloading the driver or if specifying which driver to user instead of just "version current" fixed the issue, but it's definitely improved.  I also added a fan to my case to improve cooling and so far so good.

---

### Post by reloweb on 2010-05-31
I've installed nvidia-173 drivers but the problem persist...

---

### Post by reloweb on 2010-06-03
Any news?

---

### Post by syga on 2010-06-06
Same problem. Runs too hot, fan always runs, drains batteries. 

Went back to windows, problem fixed. Runs cool.

I would prefer to use Ubuntu over Windows, however, Ubuntu is not worth damaging your laptop over.

---

### Post by kell_pt on 2010-06-27
Version 2.6.34 of the kernel solved all heat issues for me, on two computers (amd with nvidia 7000, intel with nvidia 9600)!

You can find the files here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

Quick 3 steps:

**1) Download the appropriate files into a new folder:**

If you're running 32bit version (unless you specifically chose the 64bit version, this is what you'll have), you'll need these:
- linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
- linux-headers-2.6.34-020634_2.6.34-020634_all.deb
- linux-source-2.6.34_2.6.34-020634_all.deb
- linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb

If you're running the 64bit version:
- linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
- linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb
- linux-headers-2.6.34-020634_2.6.34-020634_all.deb
- linux-source-2.6.34_2.6.34-020634_all.deb

**2) Install**
On the command line, cd into the folder and type:
$ dpkg -i *.deb

**3) Reboot**

You'll notice immediate impact.

---

### Post by kleeman on 2010-06-27
The new kernel worked for me as well. The temperature is about 3-5C cooler.
I am using the intel video driver on a Thinkpad X300. What is odd is that powertop shows double the number of wakeups with this kernel compared with the Karmic kernel I was using. In that respect it (the new kernel) is the same as the Lucid kernel but it seems to be cooler. The graphics seem quite a bit snappier as well. Suggests that the kernel side of graphics drivers is improving. It would be nice to get the wakeups down as well.....

---

### Post by reloweb on 2010-06-27
With new kernel the problem persist for me... The temp is 61°C...

---

### Post by reloweb on 2010-06-30
I've opened a new bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600375](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600375)

---

### Post by dtrot55 on 2010-07-01
Don't know if this would help...but I was having the same issue..and my fan would kick into like hardcore mode and make the loudest noise.  I took the laptop apart and low and behold my heatsinks were just loaded with dust...cleaned those out and have not had any issues...laptop is silent and computer is running perfect with 10.04.

---

