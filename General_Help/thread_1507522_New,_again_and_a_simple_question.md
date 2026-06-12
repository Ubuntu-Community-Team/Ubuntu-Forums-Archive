---
title: "New, again and a simple question"
date: 2010-06-11
forum: General Help
---

### Post by inimitablesikh on 2010-06-11
Hey everyone, I've seen mixed answers...I'm on a barebones laptop and I want to install Ubuntu linux once again. It's an OCZ DIY 15 inch laptop with a nvidia 8600m. I have 4 GB RAM and I wasn't sure if I should go with 64 bit or 32 bit...I'm ony 64 bit windows 7 so I wasn't sure how I should proceed with Ubuntu..all help is appreciated...thanks!

---

### Post by purelinuxuser on 2010-06-11
> **inimitablesikh said:**
> Hey everyone, I've seen mixed answers...I'm on a barebones laptop and I want to install Ubuntu linux once again. It's an OCZ DIY 15 inch laptop with a nvidia 8600m. I have 4 GB RAM and I wasn't sure if I should go with 64 bit or 32 bit...I'm ony 64 bit windows 7 so I wasn't sure how I should proceed with Ubuntu..all help is appreciated...thanks!

I'd say it depends on your needs.  64-bit allows you to use your processors at full capacity, so your system *may* run processor-intensive applications faster.  See [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) for more details.

---

### Post by inimitablesikh on 2010-06-11
> **purelinuxuser said:**
> I'd say it depends on your needs.  64-bit allows you to use your processors at full capacity, so your system *may* run processor-intensive applications faster.  See [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) for more details.

I was wondering if I could get newer responses as that thread is 2 years old and Ubuntu has changed....

---

### Post by X-Windows on 2010-06-11
Yes absolutely 64 bit. Should you ever need/want to add more ram 64 bit is the way to go unless Ubuntu x64 is unstable, personally I have had no issue with it. Unless you are running an older laptop 64 bit should be default.

---

### Post by quadproc on 2010-06-11
> **inimitablesikh said:**
> ...I have 4 GB RAM and I wasn't sure if I should go with 64 bit or 32 bit...I'm ony 64 bit windows 7 so I wasn't sure how I should proceed with Ubuntu..all help is appreciated...thanks!
I suggest going with the 64 bit version(s).  I have been running the 64 bit Ubuntus for more than a year and there were initially a few rough areas such as Adobe Flash but those issues have by now been fixed up.  Larger disks and larger RAM will be used by new applications and 32 bit won't work for these new applications.

64 bit is clearly the future; 32 bit is becoming legacy.  I do not think that this market will ever go to 128 bit architectures; look at Intel's Itanium.  Instead, I expect to see lots and lots of 64 bit processors in a single chip, with some kind of intelligent interconnect to allow mass parallelism.  It will be a while before that happens.

quadproc

---

### Post by inimitablesikh on 2010-06-16
> **quadproc said:**
> I suggest going with the 64 bit version(s).  I have been running the 64 bit Ubuntus for more than a year and there were initially a few rough areas such as Adobe Flash but those issues have by now been fixed up.  Larger disks and larger RAM will be used by new applications and 32 bit won't work for these new applications.

64 bit is clearly the future; 32 bit is becoming legacy.  I do not think that this market will ever go to 128 bit architectures; look at Intel's Itanium.  Instead, I expect to see lots and lots of 64 bit processors in a single chip, with some kind of intelligent interconnect to allow mass parallelism.  It will be a while before that happens.

quadproc

I want flash to work well. Are you saying that it works well and the problems are fixed on 64 bit now? As far as I know 64 bit Ubuntu and flash were having problems.
Also, I use skype quite a bit, and that includes the video chat. Would that also have problems?


Also, I am dual booting Windows and Mac(this was a test that will be removed, but for now it's there). If I install Ubuntu, how will that affect my bootloader? Right now I use Windows bootloader and it defaults to Windows 7 which is the way I want it.

---

### Post by B-80 on 2010-06-16
> **inimitablesikh said:**
> I want flash to work well. Are you saying that it works well and the problems are fixed on 64 bit now? As far as I know 64 bit Ubuntu and flash were having problems.
Also, I use skype quite a bit, and that includes the video chat. Would that also have problems?


Also, I am dual booting Windows and Mac(this was a test that will be removed, but for now it's there). If I install Ubuntu, how will that affect my bootloader? Right now I use Windows bootloader and it defaults to Windows 7 which is the way I want it.

You'd install grub and pick which OS to boot into. Shouldn't be a problem...

I am on 64 bit 9.10 and I have no trouble with flash or skype video chat.

---

### Post by inimitablesikh on 2010-06-16
> **B-80 said:**
> You'd install grub and pick which OS to boot into. Shouldn't be a problem...

I am on 64 bit 9.10 and I have no trouble with flash or skype video chat.

Awesome. I'm going to install 10.04 shortly. How should I install the flash that's compatible with 64 bit, and same with skype.

Also, how should I install all the necessary drivers? I can connect via ethernet to get a connection if wireless doesn't work. But, how should I go from there?

---

### Post by inimitablesikh on 2010-06-18
Alright, so I just installed Ubutnu 10.04, and it's pretty awesome. First things first, it's 64-bit, and it will not enter sleep mode when I press suspend. The laptop stays on at a black screen with a window that let's me enter my password to unlock, basically the lock screen. This was after a fresh install, so I tried installing my nVidia graphics card restricted drivers and I'm still having the same problem. Any idea?

---

### Post by jxtreme on 2010-06-18
> 
        Alright, so I just installed Ubutnu 10.04, and it's pretty awesome.  First things first, it's 64-bit, and it will not enter sleep mode when I  press suspend. The laptop stays on at a black screen with a window that  let's me enter my password to unlock, basically the lock screen. This  was after a fresh install, so I tried installing my nVidia graphics card  restricted drivers and I'm still having the same problem. Any idea?     Check this bug out: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/587180](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/587180)

---

### Post by inimitablesikh on 2010-06-18
> **jxtreme said:**
> Check this bug out: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/587180](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/587180)

How is that supposed to help me or are you just trying to get your post count up? =x

Again,
Alright, so I just installed Ubutnu 10.04, and it's pretty awesome. First things first, it's 64-bit, and it will not enter sleep mode when I press suspend. The laptop stays on at a black screen with a window that let's me enter my password to unlock, basically the lock screen. This was after a fresh install, so I tried installing my nVidia graphics card restricted drivers and I'm still having the same problem. Any idea?

---

