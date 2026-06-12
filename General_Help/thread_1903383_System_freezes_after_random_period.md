---
title: "System freezes after random period"
date: 2012-01-02
forum: General Help
---

### Post by dj.houba on 2012-01-02
Hello,
I have new PC with Linux Kubuntu 11.10. After some random (1m - 2h+) period my PC completly freezes. I have to use HW restart. I want to ask, how to find, where is the problem? And I will need your help to solve this.

My HW: MB MSI P67A-GD65 (B3), CPU Intel i5 2500k, GPU ATI 6950 (MSI Twin Frozr III Power Edition/OC), HDD Corsair force 3 120GB, Memory Kingsto&#8203;n HyperX PnP 8GB &#8203;(2x4GB&#8203;) DDR3 1866.

I read, there can be some problem with old firmware in my HDD, but i flashed to the latest. I have latest BIOS. And my memtests passed without any errors. If I'am at Windows, i don't have any problems with freezing. My temperature of all components is about 52°C in max load and about 35°C in normal load.

Please, help me. Thank you!

Syslog and kernlog are attached:

---

### Post by sherric1222 on 2012-01-02
My comp also froze using ll., so i went back to 10.1 on ubuntu, and when they ask you to upgrade, don't.

---

### Post by pretty_whistle on 2012-01-02
> **dj.houba said:**
> Hello,
I have new PC with Linux Kubuntu 11.10. After some random (1m - 2h+) period my PC completly freezes. I have to use HW restart. I want to ask, how to find, where is the problem? And I will need your help to solve this.

My HW: MB MSI P67A-GD65 (B3), CPU Intel i5 2500k, GPU ATI 6950 (MSI Twin Frozr III Power Edition/OC), HDD Corsair force 3 120GB, Memory Kingsto&#8203;n HyperX PnP 8GB &#8203;(2x4GB&#8203;) DDR3 1866.

I read, there can be some problem with old firmware in my HDD, but i flashed to the latest. I have latest BIOS. And my memtests passed without any errors. If I'am at Windows, i don't have any problems with freezing. My temperature of all components is about 52°C in max load and about 35°C in normal load.

Please, help me. Thank you!

Syslog and kernlog are attached:
Freezes?

I read this on a thread about freezing:

> Power down the computer and take the battery out if it has one.  Wait 30 seconds, put the battery back in and power it on.

I had some freezing and I read this would help.

---

### Post by Bobhuber on 2012-01-02
> **dj.houba said:**
> Hello,
I have new PC with Linux Kubuntu 11.10. After some random (1m - 2h+) period my PC completly freezes. I have to use HW restart. I want to ask, how to find, where is the problem? And I will need your help to solve this.

My HW: MB MSI P67A-GD65 (B3), CPU Intel i5 2500k, GPU ATI 6950 (MSI Twin Frozr III Power Edition/OC), HDD Corsair force 3 120GB, Memory Kingsto&#8203;n HyperX PnP 8GB &#8203;(2x4GB&#8203;) DDR3 1866.

I read, there can be some problem with old firmware in my HDD, but i flashed to the latest. I have latest BIOS. And my memtests passed without any errors. If I'am at Windows, i don't have any problems with freezing. My temperature of all components is about 52°C in max load and about 35°C in normal load.

Please, help me. Thank you!

Syslog and kernlog are attached:
How much are you overclocking it ?

---

### Post by 67GTA on 2012-01-02
This problem has been popping up a lot since kernel 3.0. You might want to add your info here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335)

---

### Post by dj.houba on 2012-01-02
sherric1222: I want to reinstall system only if it will be last possible solution.

pretty_whistle: It was written about BIOS battery? Or laptop battery? Because I have desktop computer.

Bobhuber: I'm using build in overclocking from MSI matherboard (OC Genie II). But it's automatic, when it's enabled. It overclock my CPU from 3.4GHz to 4.2GHz.

67GTA: Yes, I have similar problems, like is described there. If it's my bug, I hope, it will be fix in next kernel. If not, I will need some other solution, thanks.

---

### Post by 67GTA on 2012-01-02
As of 3.1.6 it is still present. The biggest problem is that the freeze does not leave behind any logs to help debug. If it could be pinpointed, a patch could be issued for all kernels. I'm currently running 11.10 with the 2.6.39 kernel to avoid a hard shutdown 3-4 times a day. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.39.4-oneiric/")

---

### Post by dj.houba on 2012-01-03
I tried kernel 2.6.39 and I had same problems with freezes (but i didn't changed GPU drivers, they was working with old kernel).
But I discovered something. When my PC was frozen again, I tried connect via SSH. It was working. But I wasn't be able to kill KDM (xserver) or reboot. All other commands was working.
So I think, it's something with GPU or xserver. What I have to do now?

---

### Post by dj.houba on 2012-01-05
OK, I think, I solved it. I was running system yesterday and today without any freezes.
It was problem with GPU drivers. I manually instaled latest drivers from AMD web and now everything is good.

Thank you

---

### Post by repsah on 2012-01-30
> **dj.houba said:**
> OK, I think, I solved it. I was running system yesterday and today without any freezes.
It was problem with GPU drivers. I manually instaled latest drivers from AMD web and now everything is good.

Thank you

Hi, I'm a bit of a newbie, but having the same proble, where did you find the drivers and which drivers do I have to download?

Thank you.

---

### Post by 67GTA on 2012-01-30
> **dj.houba said:**
> OK, I think, I solved it. I was running system yesterday and today without any freezes.
It was problem with GPU drivers. I manually instaled latest drivers from AMD web and now everything is good.

Thank you
It still freezes with me using the 12.1 drivers from AMD. I think it is something in the newer kernels. Unity 2D and KDE without 3D effects work fine. You can get the drivers here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

