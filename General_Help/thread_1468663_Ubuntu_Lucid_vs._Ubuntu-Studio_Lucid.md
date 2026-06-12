---
title: "Ubuntu Lucid vs. Ubuntu-Studio Lucid"
date: 2010-05-01
forum: General Help
---

### Post by DeMus on 2010-05-01
Hi,
As many of you I also suffered from the desire to download and install the final version of Lucid on the 29th of April. Well, that happiness was soon over. A lot of things didn't work at all, didn't work as they should or needed to be changed even though in previous releases it was okay.

I then installed several other distro's just to find out they also didn't work. I almost believed the people who wrote me about my complaints in the forum that it could be a hardware matter.

I installed Scientific Linux, coming from CERN in Geneva Switzerland, which is based on Red Hat Linux. It didn't start at all after a successful installation. I installed Helena or Mint 8 to find out it is all very slow and also not completely functional.

But then I saw something about Ubuntu-Studio 10.04. I downloaded and installed it using the alternate installation way using RAID drives. Bamm, no way. Then again throwing away the RAID and boy was I in for a surprise::shock:
```
**[CENTER][SIZE="7"][COLOR="Red"]It works.[/COLOR][/SIZE][/CENTER]**
```
I copied my sources.list file to /etc/apt, added the keys for several repos, installed some of the standard programs I used (found out that somehow the repos showed me more programs than before), used Hardware Drivers to install the last nVidia driver which works like a charm after the reboot.
I did choose another Theme than the one Studio uses by default since in Thunderbird the menus were not usable. The text is light-grey and so is the background. I always install the Bisigi themes and chose one of those.

I am truly surprised by this OS. It gives me a lot of programs about Audio and Video, but even more it just works. I am "ready" installing and configuring it and so far no problems, no hick-ups, no crashes, no not-working programs, everything works great.

It's a long intro but here is the question: how come Ubuntu-Studio is working 100% while Ubuntu itself is far from it? It is the same computer, the same hardware, the same installer - Me.
What is the difference, what causes it?

I am very happy to have found this release, it feels good, it feels rock-solid, it looks great and until now everything just works.

I know I wrote a lot of terrible things about Lucid in earlier threads but it was the way I felt when I was trying to make it work. Now I can say: Thank you Canonical, thank you Ubuntu.
\\:D/  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/  \\:D/

---

### Post by daudag on 2010-05-01
Hi,

nice intro. Unfortunally I am in big problems with my u-studio. The fglrx for my ATI Radeon will not be installed, so I can't really compare with you. 

But for your question my experience is that it depends to the installed applications. I have a 8.10 server runing since more than a year without any bigger problem. On the other hand I've one studio installation where the sound hangs, sometimes and another (the actual killed one) which works perfectly.

So, I think there is some live in a distro packets which makes each installation unique.:^o

So, have much fun with it\\:D/

Warm Regards

Hans

---

### Post by DeMus on 2010-05-01
> **daudag said:**
> Hi,

nice intro. Unfortunally I am in big problems with my u-studio. The fglrx for my ATI Radeon will not be installed, so I can't really compare with you. 

But for your question my experience is that it depends to the installed applications. I have a 8.10 server runing since more than a year without any bigger problem. On the other hand I've one studio installation where the sound hangs, sometimes and another (the actual killed one) which works perfectly.

So, I think there is some live in a distro packets which makes each installation unique.:^o

So, have much fun with it\\:D/

Warm Regards

Hans

Thank you for your answer. Sorry to hear you have some problems with your installation. Is the hardware on the one machine eccentric, or is it really as you say the installed applications? Maybe a stupid question but ever thought about re-installing?

---

### Post by DeMus on 2010-05-02
Nobody else likes to give some comment about how it is possible that Ubuntu Lucid does not work on this computer and Ubuntu-Studio Lucid does?

---

### Post by lunaparadox on 2010-05-02
I think the kernel is the main thing thats different in studio. not sure but pretty sureish lol.

---

### Post by lunaparadox on 2010-05-02
I installed the RT kernel from the studio repo and now all works well for me in 10.04 thanks for posting that studio worked for you:guitar:

---

