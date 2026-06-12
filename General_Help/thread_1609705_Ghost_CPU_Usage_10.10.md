---
title: "Ghost CPU Usage 10.10"
date: 2010-10-30
forum: General Help
---

### Post by wakeupthesun on 2010-10-30
I'm having some issues with unknown cpu usage. It will just randomly kick in and I'll have no processes showing high CPU usage during this time, although the resource monitor shows huge spikes.

These screenshots should help you visualize what I mean. If I need to get you any info just let me know and I'll do my best. I'm new to linux and may need some guidance here. Thanks :)

ps: Pulseaudio shows a Nice of -11 in my processes list. What does that mean?

---

### Post by Rocket2DMn on 2010-10-30
Are you showing processes for all users or just your user in System Monitor?  Check the View menu.  If you want to check from the command line as well, you can run the command
```
top
```
Press q when you're finished with it.

---

### Post by wakeupthesun on 2010-10-30
oh nope, just for me. I put it on all processes, hopefully next time I can see what is causing the usage. I'll post it up when I find out. Thanks:popcorn:

---

### Post by wakeupthesun on 2010-10-30
Still doesn't appear to be showing up :\
This time it happened while I was watching netflix in virtual box. I closed virtual box and it didn't lower the cpu usage. Nothing seems abnormal in my system monitor besides the really big usage of the system moniter. The cpu usage doesn't go down with that closed either..


I have an i7 920 in my computer so any slowdown due to cpu usage is very strange. There isn't much that could put a big strain on this processor.

---

### Post by Rocket2DMn on 2010-10-30
Does the "top" command in terminal show you anything? TBH, I don't really trust the System Monitor all that much. Try with a 1 second update rate:
```
top -d 1
```

---

### Post by wakeupthesun on 2010-10-30
> **Rocket2DMn said:**
> Does the "top" command in terminal show you anything? TBH, I don't really trust the System Monitor all that much. Try with a 1 second update rate:
```
top -d 1
```

Next time It happens I'll give that a go. Shouldn't take long, seems to be happening regularly :\

---

### Post by wakeupthesun on 2010-10-30
Top isn't showing anything. Also getting a fun error in netflix now. Seriously linux is hating on me right now :(

---

### Post by Eddison on 2010-10-30
Hi guys,

I have a core i7 950 also, and the same thing is happening. When playing flightgear I notice the cpu going to 100% allot of the time, and flightgrear shouldn't tax the cpu that much. Anyway, there are no temperature issues, and everything seems to be ok. The only other thing which TOP shows is the total memory is 3.6 gb but I got 6 gb's ram ??!!
BTW like the avatar Rocket2DMn_** :)**_[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=310232")

Eddison

---

### Post by utnubuuser on 2010-10-30
Probably apt-get background update.  I noticed in Maverick that the CPU will sometimes go to 95%, and it was apt, or apt-get updating its database.

---

### Post by wakeupthesun on 2010-10-30
> **utnubuuser said:**
> Probably apt-get background update.  I noticed in Maverick that the CPU will sometimes go to 95%, and it was apt, or apt-get updating its database.

How would I go about checking to see if this is indeed the problem?

---

### Post by Kyllerss on 2010-10-31
I had a similar problem... though in my case, my stemys was practically unusable... system monitor showed a lot of CPU usage, while top didn't really reveal anything was out of the ordinary (other than the high load averages). I fixed *my* issues by upgrading to a higher kernel version (2.6.36). Here is a bug report in case you feel it may be related:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662946)

---

### Post by Omnomnom on 2010-10-31
When the Ghost CPU usage appears, did you try and reboot your machine?

---

### Post by Rocket2DMn on 2010-10-31
Are your processors scaling down their frequency? This might show a high CPU usage while your processors are scaled down.

---

### Post by wakeupthesun on 2010-10-31
> **Omnomnom said:**
> When the Ghost CPU usage appears, did you try and reboot your machine?

Yes, that and logging out (when it actually lets me) are the only way to correct the issue. It doesn't stop it from happening.


> **Rocket2DMn said:**
> Are your processors scaling down their frequency? This might show a high CPU usage while your processors are scaled down.

I'll put the applet up to see if that has anything to do with it.

Surprisingly I haven't had the problem in quite a bit now (knock furiously on wood) hopefully It stays this way. I didn't do anything to fix it though so I'm not sure why it stopped atm.

Update: The monitor is showing my CPU scaling at 59%. Although atm I'm not having any mysterious cpu usage. For your theory to be correct it would have to scale even lower. I'll keep my eye out.

---

### Post by wreckz on 2010-10-31
Ive noticed mine does that when its scaling down....

---

### Post by ulugutz on 2010-10-31
hi,
i have the same problem. 100% cpu usage but not from processes in "sudo top" or in "ps aux"
happens about 30% of the time right after login. the other 70% work great for the whole session.
has nothing to do with scaling. i can put it to fixed (max) frequency and still is 100%
started for me a little earlier than the release of meerkat :(

any help appreciated

---

### Post by Omnomnom on 2010-11-01
This appears to be a 10.x bug, if it's impacting your performance it might be time for a new processor.

---

### Post by ulugutz on 2010-11-01
it doesn't really influence the performance but it's absolutely annoying if you have this problem on a laptop. the damn fan runs the whole time.
so the cpu really does 'something' :-/

---

### Post by wakeupthesun on 2010-11-01
> **Omnomnom said:**
> This appears to be a 10.x bug, if it's impacting your performance it might be time for a new processor.

I have an i7 920. I do not think I need a new processor thank you very much :popcorn:

---

### Post by Eddison on 2010-11-01
i7 950 same problem here.. cpu going to 100% regularly :confused:

---

### Post by vsh3r on 2010-11-01
Hi,

My i5 system seems to be fluctuating around 10% usage on all 4 CPU's.  This seems kinda high to me as well.

V$H.

:popcorn:

Can someone post a Windows 7 Screenshot of a i5 or i7 running with say one program open doing NOTHING such as openoffice?  Here is how my system look on Ubuntu 10.10.

I would think the CPU usage would be around 5% at most when totally idle correct?  Why am I seeing it at about 10%?

[IMG]http://asherm.com/blog/wp-content/uploads/2010/10/Screenshot-System-Monitor.png[/IMG]

---

### Post by Eddison on 2010-11-01
Here is my CPU. Its a brand new core i7 950, and its not at 10% (I wish!)
The background is flight gear, flight simulator. Notice at the very bottom right to the picture, the numbers 123 written in red. This is the frame rate..






[IMG]http://i776.photobucket.com/albums/yy50/_eddison/Screenshot-1.png[/IMG]


Eddison

---

### Post by Rocket2DMn on 2010-11-01
Has anybody filed a bug report this? Please search existing bugs on launchpad and if you don't find one, file a new one!

---

### Post by Eddison on 2010-11-01
Ok searched for cpu usage in launchpad, and found nothing. Typed in terminal ubuntu-bug, and none of the options suited this type of bug. So i picked 'display' being the closest one Other options were sound, security, external usb. 
None of the options suited the cpu over usage, so I quite the terminal as not to send false reports etc.


Eddison

---

### Post by vsh3r on 2010-11-01
I'm running Second Life on an i5 Ubuntu 10.10 and it seems to be running with about 30% to 40% usage while idle.

Can you try to run Second Life on your i7?

(SEE ATTACHED SCREENSHOT)

V$H.

---

### Post by vsh3r on 2010-11-01
I've attached a screenshot of both TOP and SYSTEM MONITOR and it looks like TOP and SYSTEM MONITOR are in disagreement about my CPU usage.

When I check process listings in the System Monitor everything seems IDLE however the graph shows that the CPU usage is at 20%

(SEE ATTACHED)

V$H.
:(

---

### Post by ulugutz on 2010-11-02
> **vsh3r said:**
> looks like TOP and SYSTEM MONITOR are in disagreement about my CPU usage.

why do you think that? the numbers add up. so if sth. is wrong with your system at all, it's not the same as our prob with 100% cpu usage.

could it have anything to do with having 2 monitors or sometimes 2 monitors and the panels get merged on 1 screen?

---

### Post by Eddison on 2010-11-02
> Can you try to run Second Life on your i7?Yeah second life isn't a problem- runs fine. But you can see by frame rate [123fps] the chip not taxed in any way, so why the high cpu usage?? 
Kinda freaking me out... I mean I love Ubuntu but is it trying to kill my cpu?
How long have I got?


eddison

---

### Post by wakeupthesun on 2010-11-02
Mine seems to have stopped going this. I really don't know why, but a couple of things I did which could help:

Turn off auto scaling and just scale it yourself with the scaling panel applet.

make sure to use this code in terminal first:

```
sudo dpkg-reconfigure gnome-applets
```

Then left click the scaling ICON (read not the text) and change it off of the bottom options which are automatic scaling. 

Second, update your graphics driver to the newest one. I did this because of compiz crashing every now and then but it may have helped this problem, but I'm not sure. It always helps to update graphics drivers though:

Add the correct repo:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

Update:
```
sudo apt-get update
```

Upgrade:
```
sudo apt-get upgrade
```

Reboot.

I'm not sure if this will help anyone else but I haven't had the issue recently (knock on wood). I figured it could help so feel free to try it.

---

### Post by wakeupthesun on 2010-11-02
> **Eddison said:**
> Here is my CPU. Its a brand new core i7 950, and its not at 10% (I wish!)
The background is flight gear, flight simulator. Notice at the very bottom right to the picture, the numbers 123 written in red. This is the frame rate..






[IMG]http://i776.photobucket.com/albums/yy50/_eddison/Screenshot-1.png[/IMG]


Eddison

I'm not sure if the game has the option to enable multicore rendering but It looks like it's chucking all the processing for that game on your first core.

---

### Post by Eddison on 2010-11-02
Thanks wakeupthesun, I'll try this and see how I get on. However I don't want to mess with the system too much, when its working ok.
Sometimes we fix things until they break lol !
But I'd say you are spot on there- the game is not set up for multicore


ed.

---

### Post by wakeupthesun on 2010-11-02
Unfortunately this did not seem to help. I just got the ghost cpu usage again the instant I started to watch a video in totem. Therefore I think this may have something to do with pulseaudio. (I've always hated the dang thing)

Edit: As soon as I turned my CPU scaling up from 2GHZ to it's max ~2.8GHZ it stopped right away. Could be coincidental or they could be related. I'm thinking the later.

---

### Post by Eddison on 2010-11-03
Its puzzling. I stopped pulseaudio to see what effect that would have, and instead of different CPU's going to 100%, now one CPU 1 is going to 100% lol!
So in effect, killing pulseaudio seems to have loaded CPU 1 with the burden.

ed

---

### Post by ulugutz on 2010-11-04
so you have 2 cores at 100%?

or did the OS just shift the load to another core to keep the heat spread over the whole processor?

---

### Post by vsh3r on 2010-11-04
Ed...,

Another thing to try is to run the program HardInfo and benchmark your computer.  Its free on Ubuntu / Linux via the software center.  Once you run it click on Network Updater and you can compare your system to others.  

Here are some benchmarks from an i5 (Quad Core) Macbook Pro 6,2 on Ubuntu 10.10.  
**Benchmarks**

 CPU Blowfish   **This Machine**2395 MHz4.770 CPU CryptoHash   **This Machine**2395 MHz216.177
CPU Fibonacci   **This Machine**2395 MHz3.340CPU N-Queens   **This Machine**2395 MHz8.140

FPU FFT   **This Machine**2395 MHz1.588
FPU Raytracing   **This Machine**2395 MHz5.189:guitar:

V$H.

---

### Post by Eddison on 2010-11-04
Ulugutz- Nope just one core at 100% now. But check out the picture.. looks like several cores going to 100%, like one takes over from the other etc. weird huh?

V$H- cool ok hardinfo I'll try it. Didn't know it existed.. love ubuntu

ed

---

### Post by Eddison on 2010-11-04
Ok tried infohash to see what I get, and the weather looks fine...

CPU Blowfish This Machine: 2395MHz result:2.14 
CPU CryptoHash This Machine:2395MHz result:527.23
CPU Fibonacci This Machine: 2395MHz result:1.73 
CPU N-Queens This Machine: 2395MHz result:0.73

ed

---

### Post by ulugutz on 2010-11-05
ok i have seen the picture.
so what do you think is strange, that

a) you get load on only one core (that's due to shitty programming and nut using multicore tech)

b) you get 100% load but would expect only 50% or whatever due to the fact that you have a good processor (that's probably due to the fact that one core isn't as badass as all 4 of 'em)

c) you get the load jumps/changes between the cores. i can't really explain that but I know from windows that it uses different cores so that the heat of the processor is not concentrated on one spot on the die. so it jut switches the core. maybe linux does the same

---

### Post by dr_duck on 2010-11-05
I'm sure you all already know this:  

In top if you press 1 (the number 1) it'll toggle the global cpu usage between global (all cores) to individual (each core).  top's more lightweight than system monitor as well, so it's own cpu usage shouldn't distort the picture.

---

### Post by Eddison on 2010-11-05
Hi ulugutz,

> you get 100% load but would expect only 50% or whatever due to the fact that you have a good processor

Well sort of yes. All I'm concerned with is that my CPU doesn't get cooked ! I hate the idea of anything going to 100%.
But maybe this is completely normal (says ed stroking his computer).

When i disabled pulseaudio only one core went to 100%- all the time, which is worse the different cpu's going to 100% in my book.
Then one of the guys suggested some file a bug report about this- a fairly experienced member too.
Just because I am paranoid about my computer, doesn't mean there isn't something wrong with it lol!


ed.

---

### Post by ReyBrujo on 2010-11-06
I7 930 down here, have seen these spikes (that last around 2-5 minutes) since upgrading to 10.10. I used to think it was Liferea (somehow the systray icon doesn't appear anymore, so I sometimes forget I have it running), but closing it doesn't modify the spike. I noticed that sometimes killing Chromium helps (Flash in Chromium seems to spike too), but sometimes it doesn't, so it may be just a coincidence. The CPUs don't scale, though, when these spikes occur (however, the applet isn't working correctly as I don't see the numbers).

This ghost process doesn't appear in top, iotop, the graphical Gnome process viewer, nowhere.

(Edited: added screenshot about this. ALT+PrintSCR didn't work, so I just cropped it. I can give two more tips: I changed the colors in the system monitor CPU usage, and it is probably 95% system, not user. Also, at one point my network usage dropped considerably. I remember that sometimes killing x11vnc would help, but not sure if this is related).

[img]http://ubuntuforums.org/attachment.php?attachmentid=174719&stc=1&d=1289022383[/img]

---

### Post by bacardi_coke on 2010-11-06
Hey guys, just wanted to confirm this happening to me as well on my 920, every few hours i get this massive spike of stutter while listening to music, i can barely open the system monitor while that is occuring, but random cores get around 100 load, looks crazy, i wonder if Ati drivers or Alsa on the Essence ST can be the cause of this... anyway i'm going to try it on my laptop in a few days, but i doubt it's fare to compare to this configuration at all, 10.10 by the way, cheers :)

---

### Post by ReyBrujo on 2010-11-07
Looks like this one is the best matching bug. Since updating my system with the latest updates today, I haven't noticed any ghost cpu usage.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665796](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/665796)

(Edited: Actually, it happened again :( )

---

### Post by wakeupthesun on 2010-11-08
Still happening to me. Pissing me off

I want to try updated to 2.6.36 kernel but I can't find a guide of how to do this anywhere. Anyone know of a good one that can help me out?

---

### Post by jb606 on 2010-11-13
I've experienced the same issue after upgrading to 10.10, in fact it just started again!

My cpu info is pasted below and my box is up to date as of today.  The cpu spikes seem to happen when I have RhythBox running but the cpu doesn't reset back to normal after I kill the process.  The only other app that I have running right now is Firefox and gnome-terminal.  This "ghost" process has been slowing down my machine so much that my music will start skipping.

The whole event lasts for about 2-4 minutes and I do not see and out of the ordinary disk or network activity.

If any extra info would be helpful let me know.

CPU Info (/proc/cpuinfo):
vendor_id	: GenuineIntel
cpu family	: 6
model		: 26
model name	: Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz

---

### Post by lekzz on 2010-11-16
Same problem here, ntop reports high system/kernel usage but i can't seem to find what it is. Also when it happends it seems to last exactly 5 minutes in my case.

Newer kernel seem to fix it, but have worse issues on my system so i went back to .35

---

### Post by ReyBrujo on 2010-11-18
Whenever I launch a video, I get this stuff for five minutes, even if I kill the program. Then I can play videos without problem. It has to do with X or the audio system :-/

---

### Post by jb606 on 2010-11-20
Okay, this is driving me nuts!!!

I can almost trigger the CPUs to spike now.  It happens when I've got a lot of windows open and switch between them.  This has to be something with Xorg or my video card (nvidia).  The kicker is since I have no idea what process is running I can't really begin to troubleshoot.

If this keeps up I'm going to have to go back to 10.04

---

### Post by Seidr on 2010-11-25
> **jb606 said:**
> Okay, this is driving me nuts!!!

I can almost trigger the CPUs to spike now.  It happens when I've got a lot of windows open and switch between them.  This has to be something with Xorg or my video card (nvidia).  The kicker is since I have no idea what process is running I can't really begin to troubleshoot.

If this keeps up I'm going to have to go back to 10.04

I've been having the same issue ever since I installed Ubuntu 10.10 on an i7 920 server - every now and then all '8' cores jump to 90-100% usage.

I've just had a new kernel install today - hopefully that will have some effect on this issue, I'll report back if so.

The current kernel is 2.6.35-22-server - I'll be updating to 2.6.35-23.

This issue is causing havoc with a couple of hosted services!

---

### Post by Seidr on 2010-11-26
I'm happy to report that since rebooting into the new kernel, these CPU spikes have completely vanished (touch wood).

---

