---
title: "Is Ubuntu resource-hungry?"
date: 2010-05-17
forum: General Help
---

### Post by raysa on 2010-05-17
My main computer is a dual-boot laptop with an Intel dual processor (1.66 ghZ) and 2MB of RAM. When it works hard it sometimes freezes for about 10-15 secs to cool off, then carries on with what it was doing.

I've noticed that when running Windows XP this happens just a few times a day. But when running Ubuntu it's much more frequent - a few times every hour. And the freezes seem to be a little longer with Ubuntu than with XP. I'm running Lucid now, but it was just the same with Jaunty and Hardy.

Does this indicate that Ubuntu is harder work for the computer than Windows?
Is there anything I can do to reduce this?

---

### Post by jerome1232 on 2010-05-17
Windows XP is like 15 (yes I am exaggerating) years old, yes it requires less resources than a recent Ubuntu release with a full-blown Gnome Desktop Environment.


If you want Ubuntu to be easier on resources your best bet would probably to switch to a lighter desktop environment or a simple window manager.

icewm is a lightweight window manager I've always liked.

There are also some Linux distro's that are specifically made to be light, puppy Linux is a decent balance between ease of use and being easy on the resources, it uses icewm if I remember correctly.

---

### Post by cascade9 on 2010-05-17
> **jerome1232 said:**
> Windows XP is like 15 years old, yes it requires less resources than a recent Ubuntu release with a full-blown Gnome Desktop Environment.

If you want Ubuntu to be easier on resources your best bet would probably to switch to a lighter desktop environment or a simple window manager.

icewm is a lightweight window manager I've always liked.

There are also some Linux distro's that are specifically made to be light, puppy Linux is a decent balance between ease of use and being easy on the resources, it uses icewm if I remember correctly.

Windows XP isnt 15, its current 8 year old. turns 9 in august. 

You could always switch to a lighter DE, but dont try xubuntu-desktop. Its mean to be lighter, but its not that much lighter than ubuntu. 

You would be better of trying a minimal install of ubuntu (even better a minimal Xfce install) than trying things like puppy. Not that puppy doesnt work well, but those system specifications are way more than what I would consider running a lighter distro on.

---

### Post by nothingspecial on 2010-05-17
> **raysa said:**
> My main computer is a dual-boot laptop with an Intel dual processor (1.66 ghZ) and 2MB of RAM. When it works hard it sometimes freezes for about 10-15 secs to cool off, then carries on with what it was doing.

I've noticed that when running Windows XP this happens just a few times a day. But when running Ubuntu it's much more frequent - a few times every hour. And the freezes seem to be a little longer with Ubuntu than with XP. I'm running Lucid now, but it was just the same with Jaunty and Hardy.

Does this indicate that Ubuntu is harder work for the computer than Windows?
Is there anything I can do to reduce this?

I run full blown gnome, mono etc Ubuntu, smooth as a sausage, on computers with far less resources than you describe.

I think, your problem lies elsewhere.

---

### Post by philinux on 2010-05-17
> **nothingspecial said:**
> I run full blown gnome, mono etc Ubuntu, smooth as a sausage, on computers with far less resources than you describe.

I think, your problem lies elsewhere.

+1.

Could be fan or dust. Or graphics card/driver related.

---

### Post by Dayofswords on 2010-05-17
> Intel dual processor (1.66 ghZ) and 2MB of RAM
time to upgrade your RAM lol

---

### Post by leeman101 on 2010-05-17
2 MB of RAM???  maybe that was a typo.. but if not, then i would say that is definitely your problem.. LOL

---

### Post by nothingspecial on 2010-05-17
> **leeman101 said:**
> 2 MB of RAM???  maybe that was a typo.. but if not, then i would say that is definitely your problem.. LOL

You sir are eagle-eyed. I read it as GB because that was what I was expecting.

Pretty sure it`s a typo though.

---

### Post by JigglyWiggly_ on 2010-05-17
It's probably overheating and then throttling the processor.
Clean your computer.

---

### Post by bodhi.zazen on 2010-05-17
> **JigglyWiggly_ said:**
> It's probably overheating and then throttling the processor.
Clean your computer.

This ^^

I also suggest you use a more appropriate title to your threads, I almost moved this to recruiting discussions on sight.

Resource hungry comped to what would be the question, and that would be a recurring discussion debate.

Ubuntu runs on as little as 512 Mb RAM without lockups so your problem has little to do with debating "resource hungry".

---

### Post by raysa on 2010-05-18
> **JigglyWiggly_ said:**
> It's probably overheating and then throttling the processor.
Yes that was my assumption, and more or less what I meant by "When it works hard it sometimes freezes for about 10-15 secs to cool off". I was just curious that it happened more under Ubuntu than Windows, but that seems to have been answered, so thanks all.

Sorry about the memory blunder - I was wrongly quoting the L2 Cache figure (whatever that is) from the label on the computer. The RAM is 1GB.

As for "cleaning up" the computer, that sounds a good idea but as you can tell, I'm no computer-techie, and would need guidance to do that. 

And as for the thread title, I was puzzled about how the resources of my computer were apparently being strained, so it seemed a reasonable title. Resources is an ordinary word, not shorthand for human resources, but sorry for any confusion.

Thanks again all,
Ray

---

### Post by bodhi.zazen on 2010-05-18
> **raysa said:**
> As for "cleaning up" the computer, that sounds a good idea but as you can tell, I'm no computer-techie, and would need guidance to do that. 

Shut the computer off, disconnect the power cable and internet connection.

Open the case.

Use compressed air or a vacuum cleaner to remove dirt / dust, especially around vents and fan.

Close case.

Connect cables & power up.

---

### Post by mike555 on 2010-05-18
You could uncheck things in the startup list that you don't use ; like bluetooth, ubuntu one,personal file sharing, remote desktop server , visual assistance , etc.

 it's in System > Preferences > Startup applications

---

### Post by cascade9 on 2010-05-19
@ mike555- true, you can just untick them from the startup list, but its not that much harder to just uninstall them. Thats what I tend to do anyway ;) 

> **bodhi.zazen said:**
> This ^^

I also suggest you use a more appropriate title to your threads, I almost moved this to recruiting discussions on sight.

Resource hungry comped to what would be the question, and that would be a recurring discussion debate.

Ubuntu runs on as little as 512 Mb RAM without lockups so your problem has little to do with debating "resource hungry".

I agree, it prossibly is from overheating/thermal throttling, and its also pretty pointless to debate 'resource hungry'. That being said, its alomst certain that ubuntu is using more CPU resources than windows XP. (there is the chance that its cpufreq isnt setup/working right, which would explain it as well).

---

### Post by Dkkline on 2010-05-19
Reading this my first guess would be the fan, you should make a little "surgery" on it by cleaning the fan

take a vacuum cleaner and clean the fans, remember: to hold a finger on the fan while you do it, so it wont rotate

Hope you'll get it fixed

---

### Post by raysa on 2010-05-19
Thanks again folks. I'll have a go at both physical and software cleaning.

One other observation: when the freezes occur under Windows it is always accompanied by the fan audibly switching on (or maybe going to a higher speed if it's running quietly normally). But under ubuntu this very seldom happens. Would the two operating systems influence the fan-triggering differently?

---

### Post by mike555 on 2010-05-19
there are fan control programs for Windows , they set the minimum fan speed .. like this one;   [http://www.snapfiles.com/reviews/SpeedFan/speedfan.html](http://www.snapfiles.com/reviews/SpeedFan/speedfan.html)

 ... there is a program for Ubuntu called "thinkfan" , but I haven't tried it ...

---

