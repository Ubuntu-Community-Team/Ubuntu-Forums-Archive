---
title: "Problem during restarting after updated Ubuntu 9.10"
date: 2009-11-30
forum: General Help
---

### Post by csh on 2009-11-30
Before this, I upgraded from Ubuntu 9.04 to 9.10 on my laptop through alternate CD. Then I updated my Ubuntu 9.10 by using Update Manager. After update, the problem of error "Buffer i/o error on device loop0 logical block xxxxxx" was resolved, but new problem arrived.

When i try to restart my laptop in Ubuntu, It shows the Ubuntu shut down screen, then **my laptop totally freeze, my laptop monitor turned black (or turned off). My USB mouse and external USB 2.5 portable HDD's power were turned off _automatically by the system_. However, the laptop still on and the USB Cooler Fan still working, but freeze and not restarting.**

Any solution?

Edit: Attached here with a text file containing hard ware information taken with "sudo lshw >myhardware.txt" command.

---

### Post by hwttdz on 2009-11-30
Have you tried booting into the failsafe gnome? Do you even reach the grub menu?

---

### Post by u.b.u.n.t.u on 2009-11-30
Question, are you using either the ATI or Nvidia proprietary driver?

---

### Post by csh on 2009-11-30
> **hwttdz said:**
> Have you tried booting into the failsafe gnome? Do you even reach the grub menu?

The ubuntu are originally installed through Wubi. I have no problem booting into Ubuntu, but the problem occurred by restarting after using Ubuntu.

Will try to boot into Failsafe mode later.

> **u.b.u.n.t.u said:**
> Question, are you using either the ATI or Nvidia proprietary driver?

My laptop uses Intel integrated graphic (82852 / 82855).

---

### Post by u.b.u.n.t.u on 2009-11-30
csh, that is your graphics hardware, on board GPU (graphics processing unit). My question related to the drivers installed to run that.

If the drivers are ATI or Nvidia then they may be the cause of what you are describing. 

The signs to watch out for are at boot, you get to see the white Ubuntu logo, then the screen goes blank and the keyboard becomes unresponsive and one needs to switch off and on the power to restart the computer.

If that is what you are experiencing then the cause may well be the ATI or Nvidia driver.

---

### Post by csh on 2009-11-30
> **u.b.u.n.t.u said:**
> csh, that is your graphics hardware, on board GPU (graphics processing unit). My question related to the drivers installed to run that.

If the drivers are ATI or Nvidia then they may be the cause of what you are describing. 

The signs to watch out for are at boot, you get to see the white Ubuntu logo, then the screen goes blank and the keyboard becomes unresponsive and one needs to switch off and on the power to restart the computer.

If that is what you are experiencing then the cause may well be the ATI or Nvidia driver.

I never use any ATI or Nvidia proprietary driver on my laptop because I am not using Nvidia nor ATI video card on my laptop,

> **hwttdz said:**
> Have you tried booting into the failsafe gnome? Do you even reach the grub menu?

There is no failsafe gnome in grub menu. I installed Ubuntu through Wubi, then upgraded to 9.10.

When I start my laptop, choose "Ubuntu" under Windows XP in Windows boot menu, then press ESC to go to grub menu. I found the following:

> Ubuntu 9.10, Kernel 2.6.31-15-generic
Ubuntu 9.10, Kernel 2.6.31-15-generic (recovery mode)
Ubuntu 9.10, Kernel 2.6.31-14-generic
Ubuntu 9.10, Kernel 2.6.31-14-generic (recovery mode)
Ubuntu 9.10, Kernel 2.6.28-15-generic
Ubuntu 9.10, Kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.10, Memtest86+
Other Operating System:
Windows XP Home Edition

I attached my hardware information in my first post of this thread. Kindly, please have a look.

---

### Post by u.b.u.n.t.u on 2009-11-30
So resolving your initial problem, "Buffer i/o error on device loop0 logical block xxxxxx", had the effect of creating a new problem where Ubuntu at shutdown will freeze.

Is that correct?

If so, then the fix may have changed some setting related to shutting down Ubuntu. Does that sound like it could be the problem?

---

### Post by csh on 2009-11-30
> **u.b.u.n.t.u said:**
> So resolving your initial problem, "Buffer i/o error on device loop0 logical block xxxxxx", had the effect of creating a new problem where Ubuntu at shutdown will freeze.

Is that correct?

If so, then the fix may have changed some setting related to shutting down Ubuntu. Does that sound like it could be the problem?

I am not sure about that. But, if I shut down Ubuntu, the computer totally shut down and the whole laptop turned off. That mean I am able to shut down my laptop successful. But, problem occur on reboot/restart.

I edited my first post in this thread. You may read it again.

I reported this bug. [https://bugs.launchpad.net/ubuntu/+bug/490204](https://bugs.launchpad.net/ubuntu/+bug/490204) .

---

### Post by u.b.u.n.t.u on 2009-11-30
I read your launchpad report. It seems that the process to shut down Ubuntu has become corrupted.

Short of finding a fix, a reinstall may give the least headaches.

Is the following site relevant?
[http://www.fixya.com/support/t883139-ubuntu_doesnt_shut_down](http://www.fixya.com/support/t883139-ubuntu_doesnt_shut_down)

---

### Post by csh on 2009-11-30
> **u.b.u.n.t.u said:**
> I read your launchpad report. It seems that the process to shut down Ubuntu has become corrupted.

Short of finding a fix, a reinstall may give the least headaches.

Is the following site relevant?
[http://www.fixya.com/support/t883139-ubuntu_doesnt_shut_down](http://www.fixya.com/support/t883139-ubuntu_doesnt_shut_down)

I'm now trying to reinstall Ubuntu through Wubi, then reinstall all the updates.

If reinstall does not fix the problem, that mean there is a problem with the updates I installed before.

If reinstall does fix the problem, then may be there is a problem upgrading from old version to 9.10. I hope that Ubuntu developers will take this seriously.

It is night time here in my country now. I will post the result either by tonight or tomorrow.

---

### Post by csh on 2009-11-30
> **u.b.u.n.t.u said:**
> I read your launchpad report. It seems that the process to shut down Ubuntu has become corrupted.

Short of finding a fix, a reinstall may give the least headaches.

Is the following site relevant?
[http://www.fixya.com/support/t883139-ubuntu_doesnt_shut_down](http://www.fixya.com/support/t883139-ubuntu_doesnt_shut_down)

I successfully reinstalled Ubuntu 9.10 but not applying any updates yet.

The problem still exist. Any suggestions?

---

### Post by u.b.u.n.t.u on 2009-11-30
> **csh said:**
> I successfully reinstalled Ubuntu 9.10 but not applying any updates yet.

The problem still exist. Any suggestions?

Yes, install Ubuntu 9.04, do not apply updates, and see what the result is.

---

### Post by csh on 2009-11-30
> **u.b.u.n.t.u said:**
> Yes, install Ubuntu 9.04, do not apply updates, and see what the result is.

Reinstalled Ubuntu 9.04. There is no problem restarting Ubuntu when using Ubuntu 9.04 on my laptop.

The problem occur only on Ubuntu 9.10, and only on my Laptop. Other computers have no problem running Ubuntu 9.10.

However, no problem when using Ubuntu 9.04 on my laptop.

But, still hope the bug will be fixed.

---

### Post by u.b.u.n.t.u on 2009-12-01
You reported the bug(s) to launchpad, isolated the cause as being related to 9.10, can use 9.04, so all in all a good outcome.

Now to wait until 9.10 is updated so that you can use it as intended.

---

### Post by csh on 2009-12-01
> **u.b.u.n.t.u said:**
> You reported the bug(s) to launchpad, isolated the cause as being related to 9.10, can use 9.04, so all in all a good outcome.

Now to wait until 9.10 is updated so that you can use it as intended.

I would like to ask some questions.

May the problem related to ACPI in Ubuntu 9.10?

My laptop and all my other computers are ACPI based system. I reinstalled Ubuntu 9.10 on my laptop again to try to solve the problem.

When I try to edit the grub boot option during booting and add "acpi=off" command then boot the Ubuntu. The restart problem was gone but cause a lot of other problems like the following:
1. Cannot activate my WiFi
2. During shut down, the laptop will not turn off automatically and I have to manually turn off myself.

I cannot permanently make my Ubuntu 9.10 boot with "acpi=off" because it will cause my internal WiFi adapter cannot be activated, so my Ubuntu must boot WITHOUT "acpi=off" command.

So, may the problem related to ACPI in Ubuntu 9.10?

---

### Post by u.b.u.n.t.u on 2009-12-01
> **csh said:**
> May the problem related to ACPI in Ubuntu 9.10?

I don't know. I wouldn't like to speculate but ACPI is not new and it is an essential function in modern computers.

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

I would think that contacting the relevant developers working in this area would be the next logical step.

That you have first hand experience of this matter and are able to test for solutions would be an asset to an eventual permanent solution.

Ubuntu is being developed at a break neck speed, and although we do suffer the quirks and bugs that are associated with such an adrenalin rush development rate, I would have it no other way. The  problems will be resolved and we will get a maintain stream operating system at the end of the day.

Ubuntu is reinventing the wheel ... making it round!

---

### Post by csh on 2009-12-01
> **u.b.u.n.t.u said:**
> I don't know. I wouldn't like to speculate but ACPI is not new and it is an essential function in modern computers.

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

I would think that contacting the relevant developers working in this area would be the next logical step.

That you have first hand experience of this matter and are able to test for solutions would be an asset to an eventual permanent solution.

Ubuntu is being developed at a break neck speed, and although we do suffer the quirks and bugs that are associated with such an adrenalin rush development rate, I would have it no other way. The  problems will be resolved and we will get a maintain stream operating system at the end of the day.

Ubuntu is reinventing the wheel ... making it round!

Really appreciate for all your replies. Thank you! I will continue to wait for the fix.

---

### Post by u.b.u.n.t.u on 2009-12-02
You are welcome. I am waiting for updates too before I can use Ubuntu. All the best.

---

### Post by markus_p on 2009-12-02
Hallo All,

I have the same problem with a HP Pavalion k842.de: Shutting down Ubuntu 9.10 works fine. Next restart hangs with a blue HP-Screen. After unplugging and replugging the power cord the systems restarts correct.

Regards,

Markus

---

