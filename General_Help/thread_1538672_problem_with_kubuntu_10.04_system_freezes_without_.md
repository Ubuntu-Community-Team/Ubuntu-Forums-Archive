---
title: "problem with kubuntu 10.04: system freezes without nolapic,  can't get SMP working"
date: 2010-07-25
forum: General Help
---

### Post by pedro6893 on 2010-07-25
Well, I'm building a new system, and yesterday I tried to install kubuntu, but could only get it running using the nolapic option (noapic is not nescessary, and noapic without nolapic won't work).

Now I have the system installed but can only get it running using nolapic and therefore without SMP (which is a no go for most people, including me).

When I try to boot without nolapic, the system goes just fine through loading the kernel and kubuntu (that is, until the end of kubuntu's loading screen), but when it's done with loading it displays the login screen and freezes completely. No input or activity whatsoever. Sysrq keys seem not to work either.

I've searched for similar problems but had little luck so far. I'm using a ga-p55m-ud2 mobo, core i3 530 (2 cores with HT) and an HD5770 (if this is relevant at all). I was hoping some of you experienced users could suggest some kind of workaround to the problem (maybe the kernel is configuring the lapics towards a lockup?) or instruct me as to how could I know what the system was doing right before stopping, in order to locate more specifically what's the problem.

I've never used linux as my main operating system (trying to migrate to it now), but I have some notion of it, even though I don't quite know how everything works, so I might not be familiar with some commands or parts of the system operation..   (luckily I have internet and google and that shouldn't be a real problem)

thanks in advance

---

### Post by pedro6893 on 2010-07-26
The problem went away spontaneously. I changed my keyboard from ps2 to a usb one, rebooted without nolapic and left the computer alone (didn't wait for login screen). When I came back about two hours later it was running using all 4 threads,  subsequent boots worked normally. I don't know if the keyboard had any relevance at all, as the old keyboard could also be used normally if plugged in.

---

