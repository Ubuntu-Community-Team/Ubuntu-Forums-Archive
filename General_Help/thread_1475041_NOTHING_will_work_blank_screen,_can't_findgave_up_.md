---
title: "NOTHING will work: blank screen, can't find/gave up on root.disk, live cd won't boot"
date: 2010-05-06
forum: General Help
---

### Post by robot85 on 2010-05-06
This is REALLY making me mad. I have been trying to get Ubuntu to work for the past 2 weeks now. I'm having QUITE a few problems.

It is installed with wubi.

1) I cannot get into Ubunutu at all. A few things happen when booting:
          a) It says "Gave up on finding root.disk"; I know how to fix THIS (sort of), I just press reboot and it doesn't usually come up next time.

          b) Once I get past that, Ubuntu tries to boot but there is just a blank screen and there is no startup sound or anything. My monitor seems to stop responding to anything (no white box comes up when I turn it off/on again). So what I did to see if it would work, I unplugged the monitor and plugged it back in; it starts flashing saying "Input signal out of range. Recommended setting: 1280x1024 60hz". I searched around the forums and found out what I think the solution is: configure the X file or whatever -- but I can't do that. I press all sorts of key combos to get into a terminal, but nothing works. Just sits there, blank screen, no sound, nothing.


My second problem:

2) If I put in the live cd to try to attempt to fix this garbage, it starts to boot, then just blank screen. Same as wubi Ubuntu trying to boot. Nothing.

3) I tried booting into recovery mode to see if I could configure the X file that way... I pick recovery mode from grub and it comes up with a whole buncha lines, then the "cannot find root.disk/gave up on finding root.disk". I type exit a few times, doesn't work, so I type reboot, and it usually gets past that screen the 3rd time.

Then blank screen. Same thing. Monitor doesn't respond. I can't boot into ANYTHING Ubuntu, whether it be the Wubi installation, the live cd, the recovery mode, NOTHING.


I would really, REALLY appreciate some help on this, as my other thread has been ignored, and I really want to use Ubuntu. Thank you very much. :p

---

### Post by 405jayb on 2010-05-06
Not sure if this helps but I had a problem kinda like that and it turned out to be the cd drive. Try cleaning or a different one if you can. Sorry if this doesnt help.

---

### Post by Twitch6000 on 2010-05-06
This is an issue that canonical decided to release with.

Read more about it at - [http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)

---

### Post by robot85 on 2010-05-06
Okay. Thank you for replying. I will try installing 9.10 Karmic with wubi and see if that works. But if I upgrade to 10.04 with the updater in Ubuntu, will I face the same problems?

Another thing to mention -- my processor is an AMD Athlon 64 X2. I used the Intel (i368 or whatever) cd. Are these problems being caused by that? A friend told be I should go ahead and use the i368 cd because my computer only has 1GB of memory. So I did.

I will try Karmic and post my results. Thanks! :p

---

### Post by 405jayb on 2010-05-06
Try it via command line. 
Check out this page.
[http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html](http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html)

---

### Post by Twitch6000 on 2010-05-06
> **robot85 said:**
> Okay. Thank you for replying. I will try installing 9.10 Karmic with wubi and see if that works. But if I upgrade to 10.04 with the updater in Ubuntu, will I face the same problems?

Another thing to mention -- my processor is an AMD Athlon 64 X2. I used the Intel (i368 or whatever) cd. Are these problems being caused by that? A friend told be I should go ahead and use the i368 cd because my computer only has 1GB of memory. So I did.

I will try Karmic and post my results. Thanks! :p

There is no need to use the 64bit if you only have 1gb of ram. Also if you upgrade from karmic the same problem will happen.

---

### Post by robot85 on 2010-05-06
Oooooof course it will. I guess I will be stuck with Karmic. Provided it actually works. Which I doubt it will. But thanks for your help. :)

So there is no way to fix the 10.04 problem?

---

### Post by Twitch6000 on 2010-05-06
> **robot85 said:**
> Oooooof course it will. I guess I will be stuck with Karmic. Provided it actually works. Which I doubt it will. But thanks for your help. :)

So there is no way to fix the 10.04 problem?

Not that I know of. It probably won't be fixed until canonical fixes the problem or a third party that does care fixes it.

---

### Post by robot85 on 2010-05-06
Then I'll just pray that Karmic works, which, I'm downloading now. But if I get the same problems, it may not be a 10.04 bug, but I need to stop saying if and just try. Thanks for your help.

---

### Post by Twitch6000 on 2010-05-06
> **robot85 said:**
> Then I'll just pray that Karmic works, which, I'm downloading now. But if I get the same problems, it may not be a 10.04 bug, but I need to stop saying if and just try. Thanks for your help.

Another suggest I have is try another distro. Opensuse and Mandriva are good ones.

---

### Post by robot85 on 2010-05-06
Yeah. But I can't install them with something like the wonderful wubi. Which sucks. I have no sweet clue on how to partition, and there are way too many risks involved in it. I have an extra old 10GB hd that we got from an old computer we found in a dump though. But I'm afraid of ruining/deleting everything on the computer. I have waaaaay to much stuff to lose. And my sister uses it as well.

---

### Post by robot85 on 2010-05-06
9.10 Karmic WORKS!!!!! I'm so happy!! But there are two things I need to change:


1) The screen resolution settings will not let me go higher than 800x640 or whatever the exact numbers are. I tried editing the xorg.config, but it is blank.

2) The package updater starts itself and want to install updates. How do I turn this off?


Thank you!

---

### Post by robot85 on 2010-05-06
:KS

Woohoo!! :p

Updating my graphics card driver fixed the screen res problem... awesome!!! Thank you for your help!


Now to not upgrade to 10.04. It's too bad though, cause I liked it. But at least this works!!!


):P

---

### Post by Catharsis on 2010-05-06
Grats on getting Karmic to work. It's rock solid; you're gonna love it :)

Anyway, do you mind entertaining a curiosity of mine? Could you post the output of:
```
lspci | grep VGA
```

Have a good one.

---

### Post by robot85 on 2010-05-06
Thanks. :p

I already got some amazing themes and all that. I love it.

I can do that tomorrow, right now I'm in bed typing this to you on my iPod Touch, but I'll be sure to do it tomorrow and post the output.

Why exactly do you want me to do that? What does it do (just outta curiosity)?

---

### Post by robot85 on 2010-05-06
Thanks. :p

I already got some amazing themes and all that. I love it.

I can do that tomorrow, right now I'm in bed typing this to you on my iPod Touch, but I'll be sure to do it tomorrow and post the output.

Why exactly do you want me to do that? What does it do (just outta curiosity)?

---

### Post by robot85 on 2010-05-06
Thanks. :p

I already got some amazing themes and all that. I love it.

I can do that tomorrow, right now I'm in bed typing this to you on my iPod Touch, but I'll be sure to do it tomorrow and post the output.

Why exactly do you want me to do that? What does it do (just outta curiosity)?

---

### Post by robot85 on 2010-05-06
Thanks. :p

I already got some amazing themes and all that. I love it.

I can do that tomorrow, right now I'm in bed typing this to you on my iPod Touch, but I'll be sure to do it tomorrow and post the output.

Why exactly do you want me to do that? What does it do (just outta curiosity)?

---

### Post by robot85 on 2010-05-06
Thanks. :p

I already got some amazing themes and all that. I love it.

I can do that tomorrow, right now I'm in bed typing this to you on my iPod Touch, but I'll be sure to do it tomorrow and post the output.

Why exactly do you want me to do that? What does it do (just outta curiosity)?

---

### Post by Catharsis on 2010-05-06
It just tells me what graphics card you have (lspci outputs your hardware info; grep VGA only lets it output the line with "VGA", which is the graphics part).

A bunch of people are having trouble booting Lucid because of a known-issue with Intel cards, so I'm just curious if this is another case of that or if it's something different.

---

### Post by Twitch6000 on 2010-05-07
> **robot85 said:**
> Yeah. But I can't install them with something like the wonderful wubi. Which sucks. I have no sweet clue on how to partition, and there are way too many risks involved in it. I have an extra old 10GB hd that we got from an old computer we found in a dump though. But I'm afraid of ruining/deleting everything on the computer. I have waaaaay to much stuff to lose. And my sister uses it as well.

Incorrect Opensuse does have a wubi like option. just pop in the cd and it should ask if you want to install it on windows :).

As for mandriva I think there is no install on windows for it.

but if ubuntu 9.10 is working for you then there is no need to try something else.

---

### Post by robot85 on 2010-05-07
My card is a nVidia card. But here is the output:

---

00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)

---

### Post by robot85 on 2010-05-07
Opensuse. I tried that on a Virtual Machine, and the install was all messed. It installed, but then it didn't work properly. So I gave up on it.

But I tried Ubuntu 10.04 on a VM, though. I liked it.

---

