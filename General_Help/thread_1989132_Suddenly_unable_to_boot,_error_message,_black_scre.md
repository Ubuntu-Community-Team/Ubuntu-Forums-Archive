---
title: "Suddenly unable to boot, error message, black screen, intel graphics"
date: 2012-05-28
forum: General Help
---

### Post by veroslav on 2012-05-28
Hi,

since few days ago, I am experiencing some troubles booting a Dell Laptop that has Ubuntu 12.04 (64-bit)
installed. I've been running it without any problems since Beta 2.

However, yesterday, when I tried to boot, I first got the purple screen (plymouth) and then screen became
completely black. It just sat there indefinitely, nothing helped, so I was forced to hard-reboot. No key combination (Ctrl + Alt + Fn) gave any results.

After the re-boot, I again got both the purple and then black screen. However, this time the following
error message was printed on the black screen:

```
[drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO called failed
```Again I hard-rebooted but this time into the recovery mode. From there I updated grub and restarted
through shutdown command. This time I managed to login and everything was fine. However, I managed
to catch a glimpse of an error message (assuming the same error message as above, hard to say as
it was gone too fast before I could read it completely) being printed just before the login screen
was displayed.

From this point on, I managed to shutdown and restart for about 3-4 times, and this evening I once
again got first the purple and then the black screen. I managed to solve the problem again by
running the grub update from the recovery mode.

The only thing I remeber doing before the issue started occuring is that I installed some alsa-updates,
nothing kernel-related I think.

Could anyone shed some light on what might be the cause for my problems?

I am running an Optimus laptop (HD3000 Intel/Nvidia graphics).

Thank you in advance.

---

### Post by veroslav on 2012-05-28
Actually, I had a look in the Software Centre history and I found the following update:

linux-headers-3.2.0-24-generic (3.2.0-24.38, 3.2.0-24.39)

This was installed on 25/5 and I first started noticing the problem the day after, on 26/5.

Perhaps it was something in that kernel update that is causing the issue? Does anybody knows what the update to 3.2.0-24.39 contained?

---

### Post by philinux on 2012-05-28
From grub can you boot ok from a previous kernel?

---

### Post by veroslav on 2012-05-28
Thank you for your reply, [[COLOR=#DD4814]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083").

I just tried re-booting to a previous kernel wich in my case is 3.2.0-23 and it went ok.
However, the problem does not occur each time I boot to the current kernel (3.2.0-24) so I will have to try it a few times in order to know for sure.

It seems to be a kernel bug though. I managed to find a Fedora bug report that mentions exactly the same problem and it is still unresolved.

What buffles me is that everything has been working absolutely fine for more than a month until this saturday :(

---

### Post by veroslav on 2012-05-28
And here is the bug report I believe is concerned with the same problem:

[https://bugzilla.redhat.com/show_bug.cgi?id=709115](https://bugzilla.redhat.com/show_bug.cgi?id=709115)

I also do have a SandyBridge laptop, a Intel i7 processor, and an Optimus laptop as I mentioned before. It looks as though as most of the people suffering from this problem that made a comment in the bug report above do have the same or very similar components as myself.

---

### Post by philinux on 2012-05-28
I would report the bug on launchpad using the terminal command ubuntu-bug linux and meanwhile boot from the previous kernel as a work around.

---

### Post by veroslav on 2012-05-28
That sounds as a good idea, will do that tomorrow however, as it is getting late here and I don't want to do something wrong.

I would like to thank you for your help philinux. Hopefully it gets resolved soon.

Take care.

Kind Regards,
Veroslav

---

### Post by philinux on 2012-05-28
> **veroslav said:**
> That sounds as a good idea, will do that tomorrow however, as it is getting late here and I don't want to do something wrong.

I would like to thank you for your help philinux. Hopefully it gets resolved soon.

Take care.

Kind Regards,
Veroslav

By the way you have nVidia graphics not Intel. Maybe worth purging and reinstallibg nvidia-current

---

### Post by veroslav on 2012-05-29
Hi,

no it is a nVidia/Intel Optimus combo. It you are referencing the specifications in my signature, those are for my desktop. Sorry for the confusion.

Here are the specifications for the laptop itself:

```
Intel i7-2670QM (2.20 Ghz, 6 MB, 4 cores)
nVidia GeForce GT 525M (2 GB)
6 GB DDR3 SDRAM
```

And here is the output of lspci:

```
user@user-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev ff)
```

I have installed Bumblebee in order to disable the discrete (nVidia) card, so I am using Intel card only.

---

