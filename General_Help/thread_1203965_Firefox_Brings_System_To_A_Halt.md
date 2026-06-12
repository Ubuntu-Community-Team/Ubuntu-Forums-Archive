---
title: "Firefox Brings System To A Halt"
date: 2009-07-04
forum: General Help
---

### Post by klausner on 2009-07-04
Firefox 3.0.11 is frequently bringing my system to a halt for what seems like minutes at a time. The Firefox windows grey-out, and the CPU shows 100% usage. This always happens these days trying to access Amazon, and happens randomly at other times. Sometimes when I'm not even actively doing anything in the browser!

I've searched the Mozilla forums without success. Tried all the usual about:config hacks.

Am I going to have to abandon Firefox? :(

---

### Post by lovinglinux on 2009-07-04
I don't have this problem on my desktop running Jaunty, but the same thing happens on a notebook running Intrepid. I didn't have time to troubleshoot it yet, but I suspect it could be a flash related problem. Nevertheless, the notebook has low processing power/memory, which could be contributing to this issue.

You could try to optimize your Firefox. Visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by klausner on 2009-07-04
> **lovinglinux said:**
> I don't have this problem on my desktop running Jaunty, but the same thing happens on a notebook running Intrepid. I didn't have time to troubleshoot it yet, but I suspect it could be a flash related problem. Nevertheless, the notebook has low processing power/memory, which could be contributing to this issue.

You could try to optimize your Firefox. Visit [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

As it happens, I am running Intrepid on a laptop with 1GM of RAM and a 1.1GHz Pentium-M processor.

I thought I had done every optimization out there. I looked at the thread you suggested, and I had already tried most of the things suggested, *except* the database hack. 

Didn't like the DB script in the thread you pointed to since it seemed to be using a filename in a circular manner. Found another script for the same purpose [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1088094&highlight=Database+Firefox+sqlite3"), and after I translated the error message from Croatian, I tried it.

Initial results seem fantastic! Preliminary tests show Amazon now loads in a reasonable amount of time, without hogging the whole system. 

Don't know yet if this is a complete fix, but it certainly seems like a big improvement. =D>

Thanks.

---

### Post by lovinglinux on 2009-07-04
> **klausner said:**
> As it happens, I am running Intrepid on a laptop with 1GM of RAM and a 1.1GHz Pentium-M processor.

I thought I had done every optimization out there. I looked at the thread you suggested, and I had already tried most of the things suggested, *except* the database hack. 

Didn't like the DB script in the thread you pointed to since it seemed to be using a filename in a circular manner. Found another script for the same purpose [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1088094&highlight=Database+Firefox+sqlite3"), and after I translated the error message from Croatian, I tried it.

Initial results seem fantastic! Preliminary tests show Amazon now loads in a reasonable amount of time, without hogging the whole system. 

Don't know yet if this is a complete fix, but it certainly seems like a big improvement. =D>

Thanks.

You are welcome. I'm glad it helped.

Would you mind explaining "since it seemed to be using a filename in a circular manner"?

It works for me pretty fine. Nevertheless, I know it's not an elegant code :)

> **klausner said:**
> Found another script for the same purpose [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1088094&highlight=Database+Firefox+sqlite3")

Yep. That's exactly the script I was referring to on my tutorial. I couldn't find it anymore. Thanks. I have updated my tutorial with it's link. The main difference is that my script will vacuum all profiles inside mozilla, which might include for example firefox-3.5 profiles and other mozila applications.

---

### Post by klausner on 2009-07-04
> **lovinglinux said:**
> 
Would you mind explaining "since it seemed to be using a filename in a circular manner"?


My error. I didn't read it closely enough to see there were two files with different names, not one file in both roles.

---

### Post by klausner on 2009-07-05
> **klausner said:**
> Initial results seem fantastic! Preliminary tests show Amazon now loads in a reasonable amount of time, without hogging the whole system. 

Don't know yet if this is a complete fix, but it certainly seems like a big improvement.

[SIZE="4"]**[COLOR="Red"]*WRONG!*[/COLOR]**[/SIZE]

So much for initial results. In subsequent trials the improvement disappeared. It's just as bad as originally described. I don't know why it seemed better, but even re-running the DB hack has no effect.

So I still have the original problem. Firefox is periodically sucking up all by CPU resources. :(

---

### Post by lovinglinux on 2009-07-05
> **klausner said:**
> [SIZE="4"]**[COLOR="Red"]*WRONG!*[/COLOR]**[/SIZE]

So much for initial results. In subsequent trials the improvement disappeared. It's just as bad as originally described. I don't know why it seemed better, but even re-running the DB hack has no effect.

So I still have the original problem. Firefox is periodically sucking up all by CPU resources. :(

I believe it's pulseaudio and flash. The weird thing is that the problem appears not when I open a particular web site but after a while later. For example if I open a flash game, everything goes well for a while. Flash uses a lot more CPU than regular pages, but I can play the game. Then, after a while playing the same game, the CPU usage goes to the roof and I can barely move the mouse. Firefox becomes unresponsive and depending on the situation, the only way to get out is to kill X.

This notebook is not actually used by me and I didn't tried most of [the tweaks I did on my desktop](http://ubuntuforums.org/showthread.php?t=1152095). But I removed pulseaudio today and installed esound and the problem seems to have disappeared. I will post more info tomorrow, when I will have a report if the problem is really gone or not.

---

### Post by klausner on 2009-07-05
> **lovinglinux said:**
> I believe it's pulseaudio and flash.

I don't think Amazon is using any kind of sound, nor do they use flash. I don't have noticeable problems with sites that do use flash though.

Doesn't sound like we are having the same problem.

---

### Post by lovinglinux on 2009-07-05
> **klausner said:**
> I don't think Amazon is using any kind of sound, nor do they use flash. I don't have noticeable problems with sites that do use flash though.

Doesn't sound like we are having the same problem.

Yeah, but in your case it also happens when you are not even actively doing anything in the browser, which is also weird.

I would try to remove pulseaudio anyway. I don't have it on my Desktop too and makes a lot of difference. You might also try [some other tweaks](http://ubuntuforums.org/showthread.php?t=1152095) that are not Firefox related, but also helped to improve Firefox performance.

---

### Post by lovinglinux on 2009-07-07
> **lovinglinux said:**
> I believe it's pulseaudio and flash. The weird thing is that the problem appears not when I open a particular web site but after a while later. For example if I open a flash game, everything goes well for a while. Flash uses a lot more CPU than regular pages, but I can play the game. Then, after a while playing the same game, the CPU usage goes to the roof and I can barely move the mouse. Firefox becomes unresponsive and depending on the situation, the only way to get out is to kill X.

This notebook is not actually used by me and I didn't tried most of [the tweaks I did on my desktop](http://ubuntuforums.org/showthread.php?t=1152095). But I removed pulseaudio today and installed esound and the problem seems to have disappeared. I will post more info tomorrow, when I will have a report if the problem is really gone or not.

Removing pulseaudio definitely did the trick. It goes grey sometimes, but not as usual as before and doesn't lock.

---

### Post by klausner on 2009-07-07
> **lovinglinux said:**
> Removing pulseaudio definitely did the trick. It goes grey sometimes, but not as usual as before and doesn't lock.

I don't understand. Why would removing an audio package have any effect on browser pages that don't use audio?

---

### Post by lovinglinux on 2009-07-07
> **klausner said:**
> I don't understand. Why would removing an audio package have any effect on browser pages that don't use audio?

The pages that were causing this were flash games with audio.

---

### Post by klausner on 2009-07-07
> **lovinglinux said:**
> The pages that were causing this were flash games with audio.

Well maybe yours were. Amazon, my rest case, has no audio, no flash, and no games. And FWIW, removing pulseaudio made absolutely no difference, except it was a minor PITA to reinstall ubuntu-desktop after the test.

---

### Post by lovinglinux on 2009-07-07
> **klausner said:**
> Well maybe yours were. Amazon, my rest case, has no audio, no flash, and no games. And FWIW, removing pulseaudio made absolutely no difference, except it was a minor PITA to reinstall ubuntu-desktop after the test.

UPDATE: Strike what I have said. It didn't fixed the problem, just minimized the problem.

BTW, re-installing ubuntu-desktop should be pretty simple. Which problems did you encounter?

---

### Post by lovinglinux on 2009-07-12
Just a heads up..

It seems some update reactivated the vino-server (Remote Desktop). It shouldn't be activated, because I don't use it and it is causing high CPU usage for a lot of people. I haven't even considered checking it, because I was sure it was disabled. Nevertheless, the damn thing was in the Session again. Now it seems that the problem is solved.

---

### Post by villalcalde84 on 2009-07-12
I'm using Ubuntu 8.04 and have the same problem as lovinglinux. I've noticed that after playing flash games or whatching videos, the performance of the web browser, Firefox and even Epiphany, decreases after some time, making the system really slow, and finally the system shuts down.

I had this same problem with Ubuntu 8.10 too; this is very annoying, and I hope someone has a solution or the problem gets fixed soon.

---

