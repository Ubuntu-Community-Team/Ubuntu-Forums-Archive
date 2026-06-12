---
title: "Ubuntu crashes on Thinkpad Edge 13"
date: 2011-07-21
forum: General Help
---

### Post by Idefix82 on 2011-07-21
I have 11.04 64bit installed on a Lenovo Thinkpad Edge 13, which came with no OS. All the hardware is recognised, but sometimes at irregular intervals (at least once a day), the computer just crashes. First, the screen freezes, a few seconds later it goes either blank or is filled with weird stripes. No keyboard input has any effect and cold restart is the only remaining option.

I am attaching the output of dmesg, since the last boot was after a crash. Your help will be greatly appreciated!

---

### Post by sanderj on 2011-07-21
I would do this:

- run the memory checker from the boot options to see if all memory is OK

- install ssh-server. Make you sure it works. After a crash, check from another computer on your LAN if you can still remotely log in. If so, the system has no crashed, 'only' the graphical system has ...

---

### Post by wildmanne39 on 2011-07-21
Hi, have a look at this link and see if it fixes your problem if not we will go from there.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by Idefix82 on 2011-07-21
Thank you both for the input! For the time being, I have deactivated the proprietary graphics driver (I don't care much for "full 3D potential" anyway) and will test the RAM. If the problem keeps occurring, I will try the ssh trick. In any case, I will report back.

---

### Post by nmaster on 2011-08-11
> **Idefix82 said:**
> In any case, I will report back.
Did you ever resolve the issue on your Thinkpad Edge 13? Did you try  using the 32-bit Ubuntu? Apparently that version is Certified:  [http://www.ubuntu.com/certification/hardware/201011-6824:201101-6964](http://www.ubuntu.com/certification/hardware/201011-6824:201101-6964)

---

### Post by Idefix82 on 2011-08-12
I have been planning on updating this thread and kept forgetting. Thanks for reminding me!

Yes, I did resolve the issue. The wifi driver that came with Ubuntu is buggy. Realtek supplies their own driver, which works perfectly. Since I installed it a few weeks ago, I haven't had any freezes.
So if you experience the same problem, and if the output from
```
lspci
```
contains the line
```
Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```
then you can fix the problem by following the instructions in [this post]("http://forum.ubuntuusers.de/post/3173822/") (they are in German, but almost everything is self-explanatory).

---

