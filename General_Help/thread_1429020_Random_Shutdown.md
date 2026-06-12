---
title: "Random Shutdown"
date: 2010-03-13
forum: General Help
---

### Post by tsuujin on 2010-03-13
So yesterday I upgraded kernel version to: 

Linux tsuujin 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

and was greeted shortly thereafter with a random shutdown while I was browsing the internet. No error that I could find, the system was within normal heat parameters, never happened before on my machine.

I thought it odd, but went about my business thinking it was just a bug. I walked away from my computer for the night and left it on to handle my apache server. This morning I come back to it to find it shut down, again.

So, has anyone had problems with that kernel? Is this a known issue, or suggestions on what might be causing it? It must be something to do with the upgrade, but I also upgraded several other bug-fixes at the same time, the kernel upgrade was simply the largest upgrade and I would assume it to be the source of the problem.

Help, please! Can't have my system shutting down, I rely on it to be up!

---

### Post by subedistra7 on 2010-03-13
> **tsuujin said:**
> So yesterday I upgraded kernel version to: 

Linux tsuujin 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

and was greeted shortly thereafter with a random shutdown while I was browsing the internet. No error that I could find, the system was within normal heat parameters, never happened before on my machine.

I thought it odd, but went about my business thinking it was just a bug. I walked away from my computer for the night and left it on to handle my apache server. This morning I come back to it to find it shut down, again.

So, has anyone had problems with that kernel? Is this a known issue, or suggestions on what might be causing it? It must be something to do with the upgrade, but I also upgraded several other bug-fixes at the same time, the kernel upgrade was simply the largest upgrade and I would assume it to be the source of the problem.

Help, please! Can't have my system shutting down, I rely on it to be up!

desktop?

---

### Post by tsuujin on 2010-03-13
I'm using KDE, but not the kubuntu package.

---

### Post by hansdown on 2010-03-13
Hi tsuujin.

Just wondering; why is your username included in the kernel version?

```
Linux tsuujin 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux
```

My kernel version is the same, minus that.

---

### Post by tsuujin on 2010-03-13
i think it's just a feature of uname, is it not? I know the function pulls more than just the kernel version

---

### Post by nemilar on 2010-03-13
About the uname thing, 'uname -a' will place the hostname there, as the second item.

About your other problem...

Can you do the following, to try to get an idea of exactly what is happening:

This should show some reboots.  If it doesn't (because you're logging in a lot), use "head -n 20" to show 20 lines, etc... until you see some reboots.
```
last | head
```

Look at the message logs right before the system boots up (should be what happened last, before the shutdown):
```
sudo grep "restart." /var/log/messages -B 10
```

---

### Post by tsuujin on 2010-03-13
Outputs of given commands:

tsuujin@tsuujin:~$ last | head
tsuujin  pts/0        :0               Sat Mar 13 19:31   still logged in   
tsuujin  :0                            Sat Mar 13 19:30   still logged in   
reboot   system boot  2.6.31-20-generi Sat Mar 13 19:30 - 20:55  (01:24)    
tsuujin  pts/0        :0               Sat Mar 13 10:46 - crash  (08:44)    
tsuujin  :0                            Sat Mar 13 10:46 - crash  (08:44)    
reboot   system boot  2.6.31-20-generi Sat Mar 13 10:46 - 20:55  (10:08)    
tsuujin  pts/0        :0               Fri Mar 12 20:10 - crash  (14:35)    
tsuujin  :0                            Fri Mar 12 20:10 - crash  (14:35)    
reboot   system boot  2.6.31-20-generi Fri Mar 12 20:10 - 20:55 (1+00:44)   
tsuujin  pts/0        :0               Fri Mar 12 19:33 - crash  (00:37)    
tsuujin@tsuujin:~$ sudo grep "restart." /var/log/messages -B 10
tsuujin@tsuujin:~$

---

### Post by nemilar on 2010-03-14
Thanks.  Since the second command didn't turn up anything, can you open /var/log/messages manually and find those times where it crashed, and post what happened immediately before the crash?

---

### Post by tsuujin on 2010-03-14
ok, so basically what I'm seeing from the file is a large group of entries all at the exact same time, which I assume is actually coming from the boot sequence. The last thing that shows up in each block is this:
Mar 13 19:31:06 tsuujin pulseaudio[2286]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Mar 13 19:31:55 tsuujin pulseaudio[2286]: last message repeated 6 times

I will, however, post the entire file for you to browse and see if you can find something more important.

---

### Post by nemilar on 2010-03-14
Thanks, I'll have a look.  Can you check /var/log/syslog for the same thing?  Maybe something more valuable there.

When you say that the machine shuts down, what precisely do you mean? Does the screen just go black?  Or does it actually power itself off, as if the power as been pulled?

---

### Post by tsuujin on 2010-03-14
The machine simply turns off. No shutdown sequence or warning, just a sudden power cut.

Here's the syslog, which does feature the pulseaudio line

---

### Post by nemilar on 2010-03-14
BTW, have you tried booting into the old kernel (it should be in the grub menu) and seeing if the problem still occurs?

---

### Post by rnerwein on 2010-03-14
> **tsuujin said:**
> ok, so basically what I'm seeing from the file is a large group of entries all at the exact same time, which I assume is actually coming from the boot sequence. The last thing that shows up in each block is this:
Mar 13 19:31:06 tsuujin pulseaudio[2286]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18.00 dB to 18.00 dB which makes no sense.
Mar 13 19:31:55 tsuujin pulseaudio[2286]: last message repeated 6 times

I will, however, post the entire file for you to browse and see if you can find something more important.
hi
i can't help you but for information only - you are not alone with that message about the
alsa driver, but in my case i know where it comes from. i installed:
luvcview - USB Video Class grabber for my webcam Hercules Dualpix Exchange. the cam
never works before now it works in skype and other apps. but since i had installed the software if have following messages in /var/log/messages ( only once ( but a couple of them ) when i boot the system )
Mar  2 13:11:04 tschang pulseaudio[2246]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18,00 dB to 18,00 dB which makes no sense.

but the differnce - my system don't panic. just the messages. but since i see all the posts about the update i never update since december 2009.
my kernel is:Linux tschang 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 
and i have absolutely no problems with this release ( but i'm using the shell mostely  98% ) 
ciao

---

### Post by tsuujin on 2010-03-14
> **nemilar said:**
> BTW, have you tried booting into the old kernel (it should be in the grub menu) and seeing if the problem still occurs?

i just had another shutdown (my third tonight) and i did reboot into the old kernel this time. We'll see if this helps.

A couple of things come to mind now, though:

First, every shutdown I've seen tonight has happened when I've let the computer idle for a few moments (walked away to do something), so that -may- have something to do with it. However, I do not believe the computer was idling the first time i saw the shutdown.

Second, on booting into the old kernel, i was informed that my video driver was not loading properly, and that I had to reconfigure it or boot into low-resolution mode. This happened the first time I booted into the new kernel as well, and -may- be related?

---

### Post by tsuujin on 2010-03-14
> **rnerwein said:**
> hi
i can't help you but for information only - you are not alone with that message about the
alsa driver, but in my case i know where it comes from. i installed:
luvcview - USB Video Class grabber for my webcam Hercules Dualpix Exchange. the cam
never works before now it works in skype and other apps. but since i had installed the software if have following messages in /var/log/messages ( only once ( but a couple of them ) when i boot the system )
Mar  2 13:11:04 tschang pulseaudio[2246]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 18,00 dB to 18,00 dB which makes no sense.

but the differnce - my system don't panic. just the messages. but since i see all the posts about the update i never update since december 2009.
my kernel is:Linux tschang 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:07:16 
and i have absolutely no problems with this release ( but i'm using the shell mostely  98% ) 
ciao

well, as far as I know I haven't installed that particular package, but it's interesting that the message is essentially identical.

---

### Post by tsuujin on 2010-03-14
Ok, so i just had another crash, in the middle of typing a message, on the old kernel.

---

### Post by tsuujin on 2010-03-14
Ok, so thinking it might be something with my graphics driver, I update the driver to latest version and reboot, and test the driver by running an openGL screensaver, with no problems whatsoever.

So far tonight my machine has completely rebooted 5 or 6 times now. This is very frustrating, as I can't really do anything that takes any amount of attention (such as playing games, which I would normally do on a saturday night such as this). Basically the OS is unusable, and I can't figure out any reason for the crashing.

---

### Post by tsuujin on 2010-03-14
Slightly over an hour from the last crash, i had another. Maybe some cron job?

---

### Post by lavinog on 2010-03-14
video card drivers can cause this issue...What video driver are you using?
Since you mentioned that you upgraded to the latest version, I suspect that you are using a proprietary driver...in which case you should always suspect that first.
Does the problem occur when you use a mesa driver?

---

### Post by tsuujin on 2010-03-14
> **lavinog said:**
> video card drivers can cause this issue...What video driver are you using?
Since you mentioned that you upgraded to the latest version, I suspect that you are using a proprietary driver...in which case you should always suspect that first.
Does the problem occur when you use a mesa driver?

I'm using the NVIDIA 195 drivers, which i got through the hardware drivers dialog. I could go back to the 185 and try that, i never had crashes before I switched... however i was using the 195 for quite a while before the crashes started, as far as I know.

---

### Post by tsuujin on 2010-03-14
Ok, so here's where I stand at the end of the night.

I reinstalled. Wiped my partitions, switched to kubuntu and gave it a fresh install. I simply could not handle a system that crashes regularly.

After I get everything fully updated, I start playing around online to get things back to normal for myself, and the damned system crashes again. Same thing: just goes to black screen and the PC powers off entirely.

My video card driver is now the exact same version that it was for at least a month of using ubuntu without a single crash.

I did, however, upgrade to the latest kernel again, which may be the problem. Right now, I'm booted into the first version that 9.10 of kubuntu comes with (rather than the version I updated to), and I'm going to walk away for the night. If it's off when I come back in the morning, I'm going to have to come up with some other solution, because this is just unacceptable.

---

### Post by someanon on 2010-03-14
Try leaving the media player running with music or video, see if the computer still shuts down.

---

### Post by az on 2010-03-14
I'd bet it's a hardware problem.

Have you run memtest?  CPUBurn?  How about booting a live cd from last year and letting that run?

---

### Post by tsuujin on 2010-03-14
Ok, so taking into account that the only thing I know of that just kills a computer dead like I've been experiencing is heat, I took some precautions to make absolutely certain that heat is not the problem:

Replaced the 120mm exhaust fan in the back (the new one works great, moves a lot more air than the last one) and,

Pulled off the cpu and heatsink, used thermal compound remover to clean old compound off and reapplied. Blew out heatsink, there was a bunch of dust.

I ran the bios for about 20 minutes to see the temperatures and nothing in the computer is getting above 40c now.

On a related note: is there a good thermal monitor for kde? the widget that KDE comes with always displays 40c, no matter what.

---

### Post by az on 2010-03-14
> **tsuujin said:**
> Ok, so taking into account that the only thing I know of that just kills a computer dead like I've been experiencing is heat, I took some precautions to make absolutely certain that heat is not the problem:

Replaced the 120mm exhaust fan in the back (the new one works great, moves a lot more air than the last one) and,

Pulled off the cpu and heatsink, used thermal compound remover to clean old compound off and reapplied. Blew out heatsink, there was a bunch of dust.

I ran the bios for about 20 minutes to see the temperatures and nothing in the computer is getting above 40c now.

On a related note: is there a good thermal monitor for kde? the widget that KDE comes with always displays 40c, no matter what.

I know that bad ram can cause the symptoms you are experiencing.  Actually, bad ram can mimic many hardware and especially software problems!

I've also had a faulty power supply cause intermittent cut-outs like that.  I'm sure there are more problems that can cause that, too.  My point is that since you reinstalled and tried different software without getting rid of the problem, the only other constant is the hardware.

---

### Post by tsuujin on 2010-03-14
Right, which I'm trying to pinpoint at the moment.

I'm going to run as is for a little while, and see if I get another crash. If I do, i'll have to go a bit further and see if anything else could be the problem.

---

### Post by klange on 2010-03-21
Ah, someone with the same problem is me.

I too have a machine that randomly shuts down since an upgrade to Karmic a few days ago. No heat issues, no notification, no log entries, just a random power loss.

I booted into an extremely old kernel (.28 ), and it seemed to work. I used that time to upgrade to Lucid, but after the upgrade to the .32 kernel the problem persists. I still have the old kernel and can boot into it over night to see if it resolves the problem. **e**: My .28 kernel doesn't seem to be capable of booting, so I'm on a (hopefully sufficiently old) .31-10-rt

To negate the theory that this is a video driver issue, I don't have an nVidia card - I'm on an Intel GMA945.
```
Linux tranquility 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:52 UTC 2010 i686 GNU/Linux
```

Kernel I'm running now for testing:
```
Linux tranquility 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 10:42:21 UTC 2010 i686 GNU/Linux
```

**e**: I let it run with this kernel over night, no issues. So it's definitely something introduced in the kernel between .31-10 and .31-20.

---

### Post by tsuujin on 2010-03-23
Looks like my power supply was going bad. It finally died on me entirely last wednesday, and I got a new one from newegg tonight. Everything's back up and working, no crashes so far.

---

