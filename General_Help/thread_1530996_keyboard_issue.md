---
title: "keyboard issue"
date: 2010-07-14
forum: General Help
---

### Post by agent_509 on 2010-07-14
I havent had this problem in awhile, but I just had it again today. I will be doing whatever, and suddenly the keyboard stops working. Nothing I do works, I cant type, I cant use hotkeys, nothing. And my mouse isnt much more effective. (I'd like to point out that restarting fixes the problem, but I have to use the power button) I cant click on anything on my top bar, if I hover over the power button for example, it lights up, but I cant click it. 
I don't know if I hit a hotkey or  if it's a bug, but it'd be sure nice to know how to fix it

---

### Post by salatconed on 2010-07-14
I am experiencing the same issue.
Can you take a look at your syslog file and see if there are any errors or alerts that correspond with the system locking up.

In my case the only this I see is the following entries in the sysylog file:
ul 14 13:05:49 sal-linux pulseaudio[1591]: ratelimit.c: 1482 events suppressed
Jul 14 13:12:48 sal-linux pulseaudio[1591]: ratelimit.c: 1489 events suppressed
Jul 14 13:13:48 sal-linux pulseaudio[1591]: ratelimit.c: 3737 events suppressed

I think the system may become busy trying to service the pulseaudio reuests?

Sal

---

### Post by agent_509 on 2010-07-14
I would if I could get there, but the only thing I can do with my mouse is change virtual desktops and switch to different windows. I could do a hard shutdown if you think it will help?

---

### Post by agent_509 on 2010-07-14
anyone? Please?

---

### Post by Twitch6000 on 2010-07-14
This seems to be a bug in the kernel version. I say this because alot of other distros with the same kernel have this issue.

You will need to update the kernel which can be done using the deb files found here - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.5-lucid/)

---

### Post by agent_509 on 2010-07-14
great, thanks. And how do i use these to update?

---

### Post by salatconed on 2010-07-14
> **agent_509 said:**
> great, thanks. And how do i use these to update?
If you reboot the machine and you can use the keyboard follow these steps to upgrade to the latest patches.

reboot PC
open a console to get to a command line
type in "sudo apt-get update"    (do not type the quotes )
enter your password when you are asked
type in "sudo apt-get upgrade"
answer yes if prompted

Hope that helps.
Sal

---

### Post by agent_509 on 2010-07-14
well I have everything up to date, and it just happened again. This is soooo annoying. It did it multiple times awhile back, but I've reinstalled ubuntu since then, and then it didn't do it for awhile until today, when it has done it twice so far.

---

### Post by agent_509 on 2010-07-14
help anyone?

---

### Post by agent_509 on 2010-07-15
Did it again today, can someone please help with this problem?

---

### Post by Twitch6000 on 2010-07-15
Just install the kernal I suggested. They are .deb files so it is just a double click and install.

---

### Post by agent_509 on 2010-07-16
oh, okay, I just installed them, I'll wait a couple days to see if i have the problem again.

---

### Post by agent_509 on 2010-07-16
nope, did it again, installing that kernel did nothing.

---

### Post by agent_509 on 2010-07-16
[LEFT]and it did it again, It's done it 3 times I think today. extremely annoying, I lose data because of it too.
[/LEFT]

---

### Post by Twitch6000 on 2010-07-16
Humm when you  boot are you botting into the new kernel? 

It will have a list saying ubuntu (2.6.32)
then the failse then 

ubuntu (2.6.33)

and again a failsafe.

Make sure you use the new kernel.

---

### Post by agent_509 on 2010-07-16
I think it's the new one, when I booted in the bootscreen was slightly different. I'll boot again and check

edit: yep, it's 2.6.33 so the kernel didnt fix it.

---

### Post by agent_509 on 2010-07-16
so the kernel is not the problem, anyone else have any ideas?

---

### Post by agent_509 on 2010-07-16
Im bumping this again. It's a majorly annoying issue. Should I submit a bug report?

---

### Post by simosx on 2010-07-16
Yep, report it on launchpad.net and put the link here.

I had read a few others talking about this on ubuntuforums.org.

You need to provide details of your hardware, and specifically the computer make and model.

See also
[http://ubuntuforums.org/showthread.php?t=1532535](http://ubuntuforums.org/showthread.php?t=1532535)

---

### Post by agent_509 on 2010-07-16
ok will report it, but that link you gave me is most definitely not connected. My issue is only a temporary one, it only stays in Ubuntu, and is fixed (temporarily) by a hard restart.

---

### Post by agent_509 on 2010-07-16
hp pavilion dv9700. here's the link.
[http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodClassId=-1&prodTypeId=321957&prodSeriesId=3632106](http://h20000.www2.hp.com/bizsupport/TechSupport/Home.jsp?lang=en&cc=us&prodClassId=-1&prodTypeId=321957&prodSeriesId=3632106)

all the hardware info should be there.

---

### Post by agent_509 on 2010-07-16
okay, submitted a bug report at launchpad.net and here is the link [https://bugs.launchpad.net/report-openoffice/+bug/606555](https://bugs.launchpad.net/report-openoffice/+bug/606555)

---

