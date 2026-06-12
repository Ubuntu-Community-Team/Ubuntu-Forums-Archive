---
title: "Purple screen where login should be: 10.04"
date: 2012-05-25
forum: General Help
---

### Post by Bucky Ball on 2012-05-25
Hi all, 

Title says it. Adding 'nomodset' makes no difference (nor does adding other things). I updated (NOT upgraded) 10.04, which had been working faultlessly, and attempted to install the proprietary ATI graphics driver. Didn't work, got some error I don't remember, but the machine was fine for the rest of the session. Until I switched it off; no 10.04.

I have 10.10 and 11.04 on here and they are both fine (and I can access the files and directories on the 10.04 partition). 

Boots fine, I select 10.04, get the '10.04' and start up bar of dots on a purple screen background, all as per normal, then, when I should get the login screen, all I get is a blank, purple screen. Nothing else. And no other 10.04 kernels work either (I have tried two others).

If I hit ctl+alt+F1 I get a black screen. No key combo then takes me back to the purple screen. Power button only way out. 

Any help would be great before I give up, install 10.04 minimal and go through the process of configuring that. I was just starting to tweak it up for permanent use and ditch 10.10 when this happened. That would be frustrating as I spent quite a bit of time configuring 10.04 and then trying to fix this problem when I have time over the last two weeks. Hrrmmph.  

Before anyone mentions it, no, I am not interested - yet - in installing 12.04 as my main squeeze so please don't suggest it. ;)

Tnx in advance ...

* Xubuntu 10.04 LTS
* ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

---

### Post by Haneef Mubarak on 2012-05-25
Firstly, I've had bad experiences with AMD/ATI on Linux before (just a few weeks ago, in fact). nVidia supports their stuff much, much better on Linux.

Secondly, before you progress, back up your home folder.

Just install 12.04 on and replace 10.04. Then just go with the default driver. The proprietary driver doesn't always work, and often causes more problems than it solves.

---

### Post by Bucky Ball on 2012-05-25
> **Haneef Mubarak said:**
> Just install 12.04 on and replace 10.04. Then just go with the default driver.

From my first post:

> **Bucky Ball said:**
> Before anyone mentions it, no, I am not interested - yet - in installing 12.04 as my main squeeze so please don't suggest it. ;)

Please read posts carefully ...

10.04 was working fine on default drivers so I have no reason to upgrade. If I have no option but to reinstall it will be 10.04 minimal with xfce. Here I am attempting to fix this problem - unravel what I've done - without reinstalling.

/home is already backed up and take note: I can boot 10.10 and 11.04 and access all folders in 10.04 just fine (all installs share the same /home partition anyhow) so that is not the issue. I can access the data fine. I just can't boot 10.04; I get a blank screen.

So, once more, please don't advise me to install 12.04. Please only respond if you have an idea on how to fix the purple screen where login should be that isn't reinstalling or adding 'nomodset' to the kernel line.

Carry on ... ;)

---

### Post by Haneef Mubarak on 2012-05-25
> **Bucky Ball said:**
> Please only respond if you have an idea on how to fix the purple screen where login should be that isn't reinstalling or adding 'nomodset' to the kernel line.

Carry on ... ;)

Well, if you'd like to, you could always go buy a nice nVidia card and that would likely work... ):P

---

### Post by Bucky Ball on 2012-05-25
Lol. No intention of doing that either. The one I've got works fine. This was user error. Now, back to the point ... ;)

---

### Post by rai4shu2 on 2012-05-25
Well, then. You could always try reinstalling 10.04. I'm not sure how else you fix a serious problem like that.

---

### Post by Bucky Ball on 2012-05-25
> **rai4shu2 said:**
> Well, then. You could always try reinstalling 10.04. I'm not sure how else you fix a serious problem like that.

Cheers, I probably will have to. I'm wanting the minimal install anyhow. Did one the other day so while I have it in my head ...

---

### Post by Bucky Ball on 2012-05-27
Bump ...

---

### Post by Bucky Ball on 2012-05-27
Strange thing is, boot.log tells me 'nothing has been logged yet'. Are there any other log files I should be looking at? Perhaps one concerning graphics?

---

### Post by GreatDanton on 2012-05-27
I have had the same problems like you. I had installed xfce 10.04 on my old laptop Dell Inspiron 1100, and I had problem with booting like you.

Since I don't know your computer configuration so we can just try something.

I solved my problem with this:
[http://ubuntuforums.org/showthread.php?t=1943521](http://ubuntuforums.org/showthread.php?t=1943521)

See the post 8.


Hope this helps.

---

### Post by Bucky Ball on 2012-05-28
Well, I fixed this by posting a few other threads as the problem evolved and researching some more. I removed the ATI drivers by killing fglrx. Read all about it here:

[http://ubuntuforums.org/showthread.php?t=1988686](http://ubuntuforums.org/showthread.php?t=1988686)

I can now get to the login screen beautifully. My current issue it that the mouse and keyboard are unresponsive. Read: dead. And you can read all about that and hopefully throw in some thoughts here:

[http://ubuntuforums.org/showthread.php?p=11975231#post11975231](http://ubuntuforums.org/showthread.php?p=11975231#post11975231)

I've almost resurrected my 10.04 install ... I can smell success! ;)

---

