---
title: "HP DM1Z freezes randomly"
date: 2011-12-03
forum: General Help
---

### Post by basementwall on 2011-12-03
I recently installed 11.10 on my new HP dm1z (using wubi). Most of the conversations about this machine have centered on the wireless drivers or the touchpad, but I can't find anyone (except for one blog post elsewhere) who talks about the random freezing effect.

About every other day, everything just freezes: the mouse, the programs, everything. Ctl-alt-del does nothing, so I eventually have to just turn the machine off by holding the power button. I can't find any consistent reason, as it seems to happen regardless of the number of programs open, what I'm doing, etc. (I can't remember if it happened when I was using a direct ethernet connection or if it's only when the wireless is activated.)

I know it's a longshot, but part of me wonders if it has anything to do with HP's CoolSense program, which in Windows uses some sort of (I assume?) hardware to know if the laptop is bumping around or sitting on a desk, adjusting fan power accordingly. The only reason I suggest that is because it froze once right after I moved it from my lap to the couch--a possible movement issue--and because CoolSense feels fancy enough that I know nothing about it. :)

Any ideas?

---

### Post by -Shuji- on 2011-12-24
> **basementwall said:**
> I recently installed 11.10 on my new HP dm1z (using wubi). Most of the conversations about this machine have centered on the wireless drivers or the touchpad, but I can't find anyone (except for one blog post elsewhere) who talks about the random freezing effect.

About every other day, everything just freezes: the mouse, the programs, everything. Ctl-alt-del does nothing, so I eventually have to just turn the machine off by holding the power button. I can't find any consistent reason, as it seems to happen regardless of the number of programs open, what I'm doing, etc. (I can't remember if it happened when I was using a direct ethernet connection or if it's only when the wireless is activated.)

I know it's a longshot, but part of me wonders if it has anything to do with HP's CoolSense program, which in Windows uses some sort of (I assume?) hardware to know if the laptop is bumping around or sitting on a desk, adjusting fan power accordingly. The only reason I suggest that is because it froze once right after I moved it from my lap to the couch--a possible movement issue--and because CoolSense feels fancy enough that I know nothing about it. :)

Any ideas?

Never had this problem when installing from the CD.  Have you tried it?

Shuji

---

### Post by phxnd on 2012-02-24
Same problem here. Randomly, Ubuntu freeze for a while(1 - 5 seconds). No matter what programs Im running or doing.

I've been googling for fairly and can't find how to workaround it.

Did you solve it?

---

### Post by roelforg on 2012-02-24
I'm thinking some kernel module (driver) is freezing randomly.
Give us the dmesg output when it freezes again.

---

### Post by whatever2k on 2012-05-22
It's not just Ubuntu, I have this problem on Fedora 16.

---

### Post by whatever2k on 2012-06-19
I've replicated this issue with Ubuntu 12.04 as well. 

The same system running windows 7 x64 (on another disk) works like a champ. 

I've also noted that suspend (by closing the lid) resets and returns to original point. This is somewhat of a pain, as it seems to happen several times per hour. 

I've also noted that plugging in a USB  keyboard or mouse returns functionality, but the laptop keyboard and trackpad don't return until reboot or suspend.

---

### Post by pmheideman on 2012-07-21
I've had this problem with ubuntu 11.10, 12.04, and Fedora 17, all on the same machine.  I really can't tell what is causing it, but it is driving me completely insane, since it's basically forcing me to use windows.  a worse fate is hardly imaginable.

---

### Post by whatever2k on 2012-10-31
I've done a bit more testing, and discovered that I do not have this issue under windows 7 installed from the HP recovery media. 

I also discovered that the freeze only seems to affect the local keyboard and trackpad, if I have a USB keyboard and mouse attached the system is responsive, it just won't work with the local keyboard and trackpad. 

I've updated all the HP firmware and tested again under ubuntu 12.04, and still have the problem. 

Any ideas would be wonderful.

---

### Post by hubertofliege on 2012-11-28
Similar problem.  Sometimes the mouse will still move, but usually everything stops working.  It doesn't even recognize the caps lock key.  Any music will keep playing the sound it was on when it froze.

Copied from [http://ubuntuforums.org/showthread.p...7#post12378267](http://ubuntuforums.org/showthread.p...7#post12378267)

OS: 12.10 32 bit
Laptop: Asus B53J 
Processor: Intel I5
Graphics card: ATK, I think. 

System freezes every time I use it.

Symptoms:

- Sometimes I can move the mouse, sometimes I can't.
- It happens randomly, even while browsing the internet.
- It can be a few hours after I start it up, or sooner.
- It happens invariably if I try to load music to a music player through Rhythm Box

---

### Post by hubertofliege on 2013-01-01
Did anyone in this tread eventually solve their problems?  I'm still in a serious bind.

---

### Post by whatever2k on 2013-02-19
No, I haven't seen a solution yet. So far my DM1Z 4000 has served mostly as a doorstop, as running windows isn't a legitimate option for me.

---

