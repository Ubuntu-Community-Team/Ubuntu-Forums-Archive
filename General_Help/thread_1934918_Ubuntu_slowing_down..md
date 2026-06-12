---
title: "Ubuntu slowing down."
date: 2012-03-03
forum: General Help
---

### Post by inf1nity on 2012-03-03
Here are my system specifications(As seen in System Info)-

   Memory  993.9 MiB
Processor  Intel® Core&#8482;2 Duo CPU E4500 @ 2.20GHz × 2
 Graphics  Intel® 945G x86/MMX/SSE2
  OS Type  32-bit
     Disk  8.2 GB

When i had newly installed Ubuntu(11.10 Oneiric Oncelot) with Unity, it was extremely fast. It booted up lightening fast, and shut down faster(within 3 seconds). Slowly it became slower in starting up. Yesterday i updated to Linux 3.0.0 -16-generic. 

For the past few days, Firefox was taking a lot of time in rendering web pages. Also the animation that happens when you unminimize an application from the dock, was happening very slowly. So i removed it and installed chromium. The same problem persists even now. When i open many tabs, It almost freezes. The scrolling also freezs temporarily, and sometimes even the pointer freezes.

Another problem is that, suppose music is playing, and I open a resource-intensive application, like ubuntu software centre, music starts skipping some parts and sometimes even turns off. The file keeps playing(i can see the seek pointer moving), but there's no sound.

Today i installed ClamAV and now it takes a whole minute to shut down. What's happening..?

BTW, before someone asks, here's a list of software that i installed-
VLC
Synaptic
Rhytmbox
gl-117
openJDK
Audacity
BlueJ
chromium
clamAv(along with its GUI front-end)
IDLE(using python2.7)
Ubuntu restricted extras
Wine
PlayOnLinux
CodeLite
GIMP image Editor
uGet
Deluge
qBittorrent

---

### Post by raja.genupula on 2012-03-03
Open your terminal and type ```
top
``` and look what process taking maximum load

---

### Post by inf1nity on 2012-03-03
i can't understand anything.. its all very complicated. I'm giving you the screenshot. Instead of top command, can i use System Monitor utility?
[[IMG]http://img580.imageshack.us/img580/9638/screenshotat20120303180.png[/IMG]](http://imageshack.us/photo/my-images/580/screenshotat20120303180.png/)

---

### Post by Bucky Ball on 2012-03-03
Is this just in the new kernel? If you drop back to the previous kernel is everything fast as usual? If so I'd just use the previous kernel and wait for updates to the new one ...

Are you using anything in Wine? Is that running when you are getting slow-down probs? Also, I see two instances of chromium-browse in the output of 'top'.

---

### Post by inf1nity on 2012-03-03
Okay.. so the 1 minute time for shut-down has reduced to 7 seconds. It had taken 1 minute that time maybe because it was the first power-down after installing clamAV. Whatever... that problem is solved.

As for the slow speed of browsers, lemme just reboot my system with Linux 3.0.0 -12 and check. I'll tell you as soon as i check it out.

Do you think it could be due to my not-so-capable graphics(intel 82945G)??

---

### Post by inf1nity on 2012-03-03
Well the browser is running fine for now. I'm gonna watch it for a few days and post if it remains so.

---

### Post by Bucky Ball on 2012-03-03
All sounding good so far ... if it still is in a few days please mark the thread as solved. ;)

---

### Post by inf1nity on 2012-03-03
So i just opened 11 tabs at once. Then I opened Ubuntu Software Centre. And the same problem started again. Chromium froze.

And please also provide a solution for the music problem(read my question again)..

---

### Post by Bucky Ball on 2012-03-03
I'd say the music problem is part of the same problem. Something kicks in and starts using all your resources and your music issue would be a natural consequence. If you were watching a video and the resources muncher kicked in no doubt that would also get choppy, but it's not a problem with video, per se, rather a sympton of the real problem.

---

### Post by inf1nity on 2012-03-03
> **Bucky Ball said:**
> I'd say the music problem is part of the same problem. Something kicks in and starts using all your resources and your music issue would be a natural consequence. If you were watching a video and the resources muncher kicked in no doubt that would also get choppy, but it's not a problem with video, per se, rather a sympton of the real problem.

But then why doesn't anything of this sort happen in windows? I use Windows XP pro on this same computer and this never happened to me.

I had switched to ubuntu coz i thought it would be faster and bug-free than windows.. I had never expected this to happen.. :( :(

Should I remove clamAV..? is anti-virus an unneccesary thing on a linux system..??

---

### Post by Bucky Ball on 2012-03-03
You could try removing ClamAV but was this happening before you installed it? If not, strongly advised. 

Have you tried booting into the previous kernel, as suggested? Think you need to hold down shift (or escape, depending on release) at boot and that will take you to the grub list where you can choose.

---

### Post by JC Cheloven on 2012-03-03
> **kaustbh said:**
> Should I remove clamAV..? is anti-virus an unneccesary thing on a linux system..??

The short answer is "it's not necessary at all". 
If you run an antivirus in gnu-linux is mainly because you don't want to pass infected files to other machines running windows (your friends' or relatives', etc).
In general, we don't use antivirus software over there.

---

