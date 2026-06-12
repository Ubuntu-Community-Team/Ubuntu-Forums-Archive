---
title: "Odd 100% CPU spike every half hour?"
date: 2010-01-19
forum: General Help
---

### Post by shadarack on 2010-01-19
Okay, I'm  not sure what the problem is, so I'm posting this here in General. I'll repost or move it or something if this should go somewhere else, in the meantime, I could really use some help with this!

I've been using Ubuntu for a few years now without any real problems. I've been upgrading, but not doing a fresh install for some time. Originally I installed Ubuntu with Gnome, but eventually switched to XFCE because it was lighter. Recently, I put a new SATA hard drive into my computer and shortly noticed that every half hour my system stalled out. CPU would spike to 100% and everything would stall for about 20-30 seconds or so. So after a while, I shut things down and took the hard drive back out. The CPU spikes continued. Shortly after that, my primary hard drive(also Sata) had some sort of mental melt-down and Xubuntu refused to boot past the login screen - the login splash would come up, but no login drop-down to select user. No spot to type password/user, nothing, just the splash screen background. So I'm thinking perhaps I broke something, it's been a while since I did a fresh install. So I did a fresh install of Xubuntu 9.10. The new hard-drive is still disconnected and after a bit of reinstalling softare, everything is mostly back to normal...except every half hour, regular as clockwork, my system freezes up for about 20-30 seconds as CPU goes 100%. This does not happen on the half hour and hour, and the timing is every so slightly more then half an hour(I suspect by about 20-30 seconds) so that every day this spike occurs slightly later. Rebooting seems to change when it happens, so I suspect it's some software or resource running. Cron -l shows nothing scheduled. Unfortunately, I have no clue where to even begin looking for the problem. Does anyone have any ideas?

Please help!

---

### Post by elliotbeken on 2010-01-19
i am not sure what it could be:S

do you have a cron job that runs every 30 min

i know this might be a problem because when i used to host a web server at home i had a cron job to run/calculate webalizer every 5 hours..... this would do the same to me so i then ran a cron job more often to lower the load

---

### Post by Kevbert on 2010-01-19
If you know roughly when it's going to happen, go to Terminal and type in 
```
top
```
and you should see the process/program that's causing the problem.

---

### Post by shadarack on 2010-01-19
> **elliotbeken said:**
> i am not sure what it could be:S

do you have a cron job that runs every 30 min

i know this might be a problem because when i used to host a web server at home i had a cron job to run/calculate webalizer every 5 hours..... this would do the same to me so i then ran a cron job more often to lower the load

Already checked that. Cron -l shows nothing. Unless there's someplace else I can check for Cron?

---

### Post by shadarack on 2010-01-19
> **Kevbert said:**
> If you know roughly when it's going to happen, go to Terminal and type in 
```
top
```
and you should see the process/program that's causing the problem.

Hmmm. I just tried that and it showed Virtualbox as being the culprit, which is odd because I know I was having the same problem when Virtualbox is not running. I only really notice the issue when I'm playing media - a movie or music, because the media in question hangs. I use Virtualbox to run WinXP to work and rarely ever try to run it while watching movies. Still, after work today I shall try top again when Virtualbox is not running and see what it has to say.

Is it possible that top is mis-reporting? At one point it actually showed Virtualbox as using 110% of my CPU...

---

### Post by shadarack on 2010-01-25
> **Kevbert said:**
> If you know roughly when it's going to happen, go to Terminal and type in 
```
top
```
and you should see the process/program that's causing the problem.

Hmmm. Okay, when Virtualbox is not running, Top shows no large CPU usage, but any media I happen to be playing at the time(movies, music whatever) stalls. I usually use Totem for video and Rhythmbox for music, although sometimes I use Mplayer for video. I've confirmed that all three of these programs stall. Whatever media is being played pauses, sometimes there are audio glitches. While top does not show any high usage, the system load monitor widget I have embedded in my panel shows maxed out CPU usage.

Is there some way to get a log of top's output or is perhaps there some other program that will log spikes in CPU/memory usage and report what programs caused the spike?

As a possibly related problem, I've noticed that whenever XFCE requires a system password to confirm root(for example: updating through synaptic) my system also stalls for about 20 seconds. This does not happen when I use root as a command line (for example: sudo mount -all).

Could XFCE be trying to run something as root every half hour? Is there somewhere I can check this? To my knowledge, Ubuntu only uses Cron for this, and I checked cron -l already.

This is driving me buggy!

---

### Post by danastasio on 2010-01-25
you could check the root cron?

> sudo cron -l

---

### Post by shadarack on 2010-01-26
> **danastasio said:**
> you could check the root cron?

See, that's why I asked here! I had no idea that root could have it's own separate Cron! Thank you!

I suspect my problem may have something to do with the error message I get when I do sudo cron -l

"cron: can't lock /var/run/crond.pid, otherpid may be 1207: Resource temporarily unavailable"

What does that even mean? Otherpid? 1207? I opened up cron.pid as a text file and it did indeed read 1207. Grrrr. I don't know enough about the inner workings of Linux code...

---

### Post by shadarack on 2010-01-26
> **shadarack said:**
> 
"cron: can't lock /var/run/crond.pid, otherpid may be 1207: Resource temporarily unavailable"

What does that even mean? Otherpid? 1207? I opened up cron.pid as a text file and it did indeed read 1207. Grrrr. I don't know enough about the inner workings of Linux code...

Er. Disreguard that error message, PEBCAC error. Sudo crontab -l shows nothing on sudo's cron either. So not cron or root's cron either.

Anyone have any idea why authorizing for root commands makes my window manager freeze up for 20 seconds or so, but does not freeze up at the command line? I suspect that the two problems may be one and the same...

---

### Post by lavinog on 2010-01-26
What video card do you have, and are you using a proprietary driver?

---

### Post by t4thfavor on 2010-01-26
Virtual box has a kernel module that is active at all times, perhaps it is still the culprit afterall. I have no idea how to test for this theory, but I thought I would at least put it out there.

---

### Post by shadarack on 2010-01-27
> **lavinog said:**
> What video card do you have, and are you using a proprietary driver?

I'm using a nVidia Gforce 8500 GT with whatever drivers EnvyNG installed for me.

---

### Post by shadarack on 2010-01-27
> **t4thfavor said:**
> Virtual box has a kernel module that is active at all times, perhaps it is still the culprit afterall. I have no idea how to test for this theory, but I thought I would at least put it out there.

Easy way to test - kill the kernel module and see if the CPU spike/media stall happens again. Is there some way I can check if the Kernel module is running and kill it if so? I just rebooted and see nothing virtualbox related in the processes running list of system monitor...

---

### Post by shadarack on 2010-02-01
Bump, because this is really driving me nuts and I don't know enough to even start troubleshooting what it could be...

---

### Post by Ares Drake on 2010-02-01
> **shadarack said:**
> Easy way to test - kill the kernel module and see if the CPU spike/media stall happens again. Is there some way I can check if the Kernel module is running and kill it if so?

```
lsmod
```
should list all loaded kernel modules.

```
rmmod
```
allows to unload them. modprobe -u may do the same. Have a look in the manuals, eg.
```
man rmmod
man modprobe
man lsmod

```

---

### Post by lavinog on 2010-02-01
since you are using proprietary video drivers, I would suspect the nvidia driver that envyng installed.

---

### Post by shadarack on 2010-02-03
After much poking around, I discovered that the spike always occurs when I'm running firefox. I don't know if it's firefox itself or a conflict with something else, but when I shut firefox down, the media stalls stop. I suspect firefox is doing something memory intensive every half hour and that if I purchase more phsyical memory(which I really should do anyways - I only have 1 gig of memory on a system I am running Xubuntu AND WinXP on at the same time) it may take care of the issue. In the meantime, I will try killing the virtualbox kernels and see if that takes care of the issue as well. Perhaps virtualbox and firefox are having a fight over memory or something...

---

### Post by lavinog on 2010-02-03
Try removing flash.

---

### Post by shadarack on 2010-02-04
> **lavinog said:**
> Try removing flash.

If you mean to remove the flashplugin-installer from synaptic, I did as you suggested.

Still having the issues, which is odd, because my system is reporting that I'm only using about 3/4th of my memory, so it's not running out of memory like I suspected.

Incidentally, I also tried removing all firefox add-ons and that didn't do the trick either.

---

### Post by shadarack on 2010-02-04
> **Ares Drake said:**
> ```
lsmod
```
should list all loaded kernel modules.

```
rmmod
```
allows to unload them. modprobe -u may do the same. Have a look in the manuals, eg.
```
man rmmod
man modprobe
man lsmod

```

There were three virtualbox modules still running. I removed them - no good. Every half hour, any media playing stalls while my system(and I assume firefox) does...something. No clue what either. All I know is when I turn firefox off, it stops happening. I'm going to try installing an older version of firefox if I can find one and see if that helps...

---

### Post by shadarack on 2010-02-04
> **lavinog said:**
> since you are using proprietary video drivers, I would suspect the nvidia driver that envyng installed.

Is there some way to check that and/or switch to a non-proprietary driver? I used EnvyNG because I was under the impression that it was the only way to get dual monitor output for an nVidia card - and I HAVE to have dual monitor output. I use this for work and without a dual monitor setup, I cannot work.

---

### Post by lavinog on 2010-02-04
> **shadarack said:**
> Is there some way to check that and/or switch to a non-proprietary driver? I used EnvyNG because I was under the impression that it was the only way to get dual monitor output for an nVidia card - and I HAVE to have dual monitor output. I use this for work and without a dual monitor setup, I cannot work.

I don't much experience with nvidia, but I would see if there is a more recent driver.

---

### Post by shadarack on 2010-02-05
> **lavinog said:**
> I don't much experience with nvidia, but I would see if there is a more recent driver.

Well crud. It appears there may be a new driver from nVidia itself. EnvyNG claims it gets updated drivers(after testing) via synaptic, so I probably have the most recent version from EnvyNG.

Unfortunately, I just do not know enough to remove EnvyNG and install nVidia's drivers manually - that's why I went with EnvyNG to begin with.

However, I'm really thinking the problem is with Firefox, since whenever I shut firefox down, the problem goes away. I really hope the problem is not my graphics card drivers because otherwise I'm stuck with the problem until the next update.

---

### Post by shadarack on 2010-02-05
Well, I found a newer version of firefox - version 3.6 and installed that. It did not fix the problem, but now firefox runs a lot lighter on the memory.

Does anyone know where I can get a deb of an older version of firefox(older then 3.5) or perhaps is willing to give me instructions on how to install an older version via synaptic/apt? I've removed 3.5.7 entirely and am running only 3.6.2pre for now. This has not entirely fixed the problem, although it seems to have lessened the length of the stall.

On a possibly related note, does anyone have any idea why my system stalls whenever I have to do a root authentication via the GUI? When I authorize via terminal(for example, by doing a sudo command) there is no delay, but when I do so in XFCE(for example when running Synaptic) the system freezes up for about 20 seconds.

---

### Post by lavinog on 2010-02-05
does it freeze when you use any other browsers

---

### Post by shadarack on 2010-02-12
> **lavinog said:**
> does it freeze when you use any other browsers

After extensive testing with Opera and Google Chrome, I can confirm it does not in fact freeze with other browsers.

So now the question is, what the heck is firefox doing every half hour that completely soaks my CPU cycles, and can I do anything to stop it? I'd rather not switch to another browser. Unless someone knows a way to make Opera act more like firefox...

---

### Post by lavinog on 2010-02-12
> **shadarack said:**
> 
So now the question is, what the heck is firefox doing every half hour that completely soaks my CPU cycles, and can I do anything to stop it? I'd rather not switch to another browser. Unless someone knows a way to make Opera act more like firefox...

I know firefox will save recovery data every now and then, but I think that is more like every 2 mins or something.

Also try deleting your firefox profile...it could be something there since using different versions didn't help.

---

### Post by shadarack on 2010-02-19
> **lavinog said:**
> I know firefox will save recovery data every now and then, but I think that is more like every 2 mins or something.

Also try deleting your firefox profile...it could be something there since using different versions didn't help.

What the heck? That worked. Rather then delete my profile, I moved it so Firefox couldn't find it, and the problems stopped.

So I moved the profile back with the intent of selectively deleting files until the problem goes away again, but for some reason, no more media stalling.

I don't know if an update fixed it or if the act of moving the profile and then moving it back fixed the issue, but...it's fixed?

---

### Post by zerofool2005 on 2010-02-19
My theory on life the universe and everything here. Is that firefox was trying to access that profile. For some reason couldnt. So slept for 30 mins and tried again. Hence the CPU spikes.

I could be wrong.

---

### Post by lavinog on 2010-02-19
bleachbit has a feature that vacuums the database that is stored in your profile.  Over time the database gets messy, and vacuuming it seems to give it a drastic performance boost.

Also when you moved your profile, firefox most likely created a new one.  Even though you moved the old one back, it might still be using the new one.

---

### Post by shadarack on 2010-02-25
> **lavinog said:**
> bleachbit has a feature that vacuums the database that is stored in your profile.  Over time the database gets messy, and vacuuming it seems to give it a drastic performance boost.

Also when you moved your profile, firefox most likely created a new one.  Even though you moved the old one back, it might still be using the new one.

Pretty sure that's not the case - I deleted the new profile before moving the old one back, just to be sure it would use the old profile(and thus give me all my bookmarks and cookies back!)

I may have to check out bleachbit. It sounds promising...

---

