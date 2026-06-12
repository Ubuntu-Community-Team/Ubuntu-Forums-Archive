---
title: "complete system freeze/crash, totally unresponsive, 10.10"
date: 2010-10-31
forum: General Help
---

### Post by krack3rz on 2010-10-31
First of all Maveric 10.10 is pretty awesome!
Upgraded from 10.04

Problems:
my system crashes, and quite often, I was hoping its just a small bug which would have a solution quick but I guess not...

so what happens:
screen does weird blinking, with about 5-8 horizontal strips, which sporadically disappear and appear. Also no response on/from keyboard,mouse,and alt+SysRQ+anything,except hard reboot(button still works great...).

I found this to happen most often when I leave the system for the night in "lock screen" mode and in the morning like today I turn on my monitor to find this pain in the ***...

The kernel definitely freezes...also this happened once while the comp. wasn't left on for the night, but instead just wen I left my comp alone for a little bit (don't remember if I left it on lock-sreen-mode, coulda been just turned monitor off, which I always do when I leave my comp for more than 5 min.)

I have no idea where to find log of this crash so I cant post them...
Anyway this happens very often, pretty much half the time-by that I mean night.

I am not sure if this is related but I get a lot of weird jumpy processor percentage usage when using comp, almost all the time-30% usage on some mostly used programs, firefox-bin,transmission,system monitor (-_-), etc.

I do run multiple servers...ssh,lighttpd,apache2,openbravo,vnc - which are almost always not used, problems happened before openBravo,vnc.

It may be unrelated but I get crashes on some processes-Firefox flash plug in (multiple occasions), and once "java" thats all it was called.
Info:
kernel 2.6.35-22-generic

---

### Post by DirtyPC on 2010-10-31
Have you considered running a clean install? Also are you dual booting with windows? And if so have you been doing anything with that? And the only time I experience those horizontal strips is whilst a game through Wine is loading up.

---

### Post by krack3rz on 2010-10-31
> **harrylucas1 said:**
> Have you considered running a clean install? Also are you dual booting with windows? And if so have you been doing anything with that? And the only time I experience those horizontal strips is whilst a game through Wine is loading up.

aww man, I just did a clean reinstall and can't do it again, it can only be last resort, I just did it like 3 months ago...because it kept crashing and I had memory leaks...
Theres just way too much to backup and remember what I had...it took me 2 weeks to get everything going last time xD

Anyway there cant be a problem with windows because it all worked perfectly all the time and still does, and I haven't even logged into windows for many months-more than 4 months

I have wine but I don't use it, I don't play games on this comp, I have another with most usage being windows for gaming-not much of btw xD

---

### Post by xx58 on 2010-11-01
I use Ubuntu 9.10 and it work like charm. I had problems with Ubuntu 10.4 but it was fixable. Ubuntu 10.10 my advise is: wait 2-3 month and it will be work very well. So, read, come to Ubuntu forum and learn. And .....

---

### Post by DirtyPC on 2010-11-01
I disagree, every version of Ubuntu will have its bugs, but 10.10 does work very well. Do you install lots of stuff, is it quite clustered?

---

### Post by krack3rz on 2010-11-02
What do you mean by clustered?

I do have most, almost all, of my HDD memory for / filled up with junk...less than 6 GB free from 100 GB primary partition, usually. I hope thats not y, but I have another complaint on top of that one, which I think ties into this: there are times my whole comp. freezes for like 10 sec then continues as if nothing happened, I think this usually happens when I am watching some videos.

I can only think of the kernel, being the main cause of this predicament. Because the kernel is unresponsive in these times, I cant use the sysReq + alt at all when its on the fritz...:cry:
:cry:

---

### Post by oraslaci on 2010-11-03
Same happens to me. It's very annoying. I am unable to trace the source of the problem. Logs show nothing suspicious.
Hardware config:
HP DV 6500, 32 bit, nvidia graphics (prop. drivers), maverick + latest updates.
I found this, report but it's incomplete:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/636094]("found this bug.")
Any ideas to trace this?
BTW, i have no windows.It's a clean install.It occurs without "sleeping", maybe with a bit higher probability while watching something in full screen. Found no memory errors.

Cheers,
Laszlo.

P.S. I'm happy that I'm not alone with this...

---

### Post by krack3rz on 2010-11-04
i'm glad its on launchpad now :)

maybe this should be turned over to Linus? Since the private kernel memory is overloaded then it is a fundamental problem with the kernel.

Is there a way to point this issue to the kernel team?

---

### Post by oraslaci on 2010-11-10
hello!
Do you guys by any chance use the deluge torrent client?
I use it quite often, but Yesterday I didn't have it running and my system did not freeze at all. I don't know if this really has a connection, probably after posting this my computer will hang up, without deluge, but maybe...

---

### Post by defagordi on 2010-11-10
Hello,

I have already post in a another article, the last post say that is not a kernel problem but maybe a driver problem. I have also post a picture of the "Top" command during the freeze and nothing was strange in the process list...

-> [http://ubuntuforums.org/showthread.php?p=10093758#post10090456](http://ubuntuforums.org/showthread.php?p=10093758#post10090456)

---

### Post by krack3rz on 2010-11-10
I realized that Transmission was one of the most processor hogging apps, almost always 30%. I stopped using it, and now I almost never get those freezes...
using qBittottent now xD:guitar:

Anyone like that or similar?

If so then why? transmission has always been nice an lightweight...whats happenning here?:confused:

---

### Post by hypnagogia on 2010-11-10
I'm dealing with pretty much the same problems, leaving the computer for the night in lock screen, I have no response in the morning, just a black screen, no mouse/keys working. The pc also froze twice while I was doing some random stuff. It's a fresh 10.10 install, I usually have deluge running but I think the cause of the problems are the wifi drivers. I'm using the ath5k driver. I was on a wired connection before and didn't have any problems, but on occasion when I used wireless I had the same freezes.

---

### Post by Smcdani2 on 2010-11-26
When 9.04 updates were no longer supported through the update manager I upgraded to 9.10. This is when my problems began as referenced in the title. Next I upgraded to 10.04.1 Kernel 2.6.32-25 "Same Problem No Change". I then ran update moving to Kernel 2.6.32-26 "Same Problem No Change".

 80GB SATA "WINDOWS XP HOME"GRUB BOOT LOADER INSTALLED HERE
 80GB SATA "WINDOWS 7"
320GB SATA "UBUNTU 10.10 DESKTOP"

I then decided to upgrade to 10.10 Desktop Kernel Linux 2.6.35-22-generic which made all the difference in the world. I deleted my 320GB drive which had all of my Ubuntu installs on it using cd created from ubuntu-10.10-desktop.iso which I booted the system from. My system no longer locks up or freezes. I love my linux install now.

---

### Post by defagordi on 2010-11-27
Hello,
I have upgrade the kernel to 2.36 and now no Freeze anymore, I have also install the lastupdate for my Intel graphic card.

Now everything work fine. But I can not explain exactly where are the problem.

---

