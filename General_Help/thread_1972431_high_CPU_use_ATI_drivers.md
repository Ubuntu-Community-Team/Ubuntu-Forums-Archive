---
title: "high CPU use ATI drivers"
date: 2012-05-03
forum: General Help
---

### Post by blackløtus on 2012-05-03
hi guys!

Last week my old nvidia graphic card was died. Then I installed the ATI drivers for work with the onboard ATI RADEON HD 3200 graphic card. 
The problem is that since then the CPU consumtion is very high without any processes runnning, and when I do a work that uses the graphic card like play a video the CPU works really hard.
I can see in the TOP the Xorg process in the "top" without moving all the time.

specifications:
ubuntu 10.04 lts 32 bits
kernel: 2.6.32-40-generic
ati driver: 010.087.000.001.000000
CPU: AMD Athlon x2
Graphic card: onboard ATI RADEON HD 3200

any suggestion?
some body had the same problem with ATI drivers?

---

### Post by electrojustin on 2012-05-03
I have some experience with the Radeon series (4200), are you using the fglrx from the repos or did you download the driver from the ATI website? The one in the repos is very outdated and rather buggy.

---

### Post by MonkeyPaw on 2012-05-03
How are you monitoring CPU usage? If it's with System Monitor, go over to the processes tab and sort descending by %CPU. At the top will be your big users. Sadly, System Monitor is often the culprit! I've also seen Python bog it down from not closing correctly.

As for the HD 3200, it's just not a powerful solution compared to even a modest dedicated card. You CPU is doing all the processing when it comes to video.

---

### Post by blackløtus on 2012-05-04
> **electrojustin said:**
> I have some experience with the Radeon series (4200), are you using the fglrx from the repos or did you download the driver from the ATI website? The one in the repos is very outdated and rather buggy.

I downloaded the driver from the ATI's web page and generate a distribution specific driver package

[QUOTE=MonkeyPaw].....[/QUOTE]

With the top command in a terminal.
About the 3200 HD I know that, it's a temporary solution. But a I want that it work fine anyway

thanks for your suggestions

---

### Post by electrojustin on 2012-05-04
Wait, you clicked the generate distribution specific package button? That doesn't install anything afaik. You want to click the first option when you run the installation ".run" file.

---

### Post by MonkeyPaw on 2012-05-04
You don't want to do a distribution specific install. Choose the other option. If you run into compatibility issues (like it says no supported card), you might try older versions of Catalyst. The option to download old versions is linked below when you get to the 12.4 click-to-download page.

---

### Post by blackløtus on 2012-05-05
@electrojustin @MonkeyPaw I generated the .deb packages and installed it. I thought that generate the packages create a more optimized packages for my hardware...

Anyway I have just uninstalled it and clicked the install option. Maybe the CPU consumption has decreased a bit.
But why you think that the generated packages are bad?

---

