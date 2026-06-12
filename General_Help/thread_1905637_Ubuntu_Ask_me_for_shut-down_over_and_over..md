---
title: "Ubuntu Ask me for shut-down over and over."
date: 2012-01-07
forum: General Help
---

### Post by qsebas on 2012-01-07
Hi, Last year I have bought an HTPC, resized his w7 partition and installed Ubuntu on it (now evolved to 11.10).

The main software I use is XBMC axed out to watch movies and listen music, but sometimes I minimize XBMC and use a browser or other programs.

Since about september, as soon I minimize XBMC (it can be running for weeks) I start to get the "System is about to shut-down" windows over and over and over. No matter if I press the CANCEL button, I get immediatly the windows again.

It is very annoying, because this situation can last for 2 minutes or for 15 minutes, and don't let me do anything in my system, if I simply move the windows again, my system get shuted down at 60 seconds.

I don't have any Idea on what is triggering the shut-down, neither wich log to rad to have a clue on what is happening.

The only solution I'm figuring is reinstalling ubuntu, but its a thing that i wich really to avoid.

can anyone help me on figuring what can be the problem?

thanks a lot

Sebastian from Argentina

---

### Post by Basher101 on 2012-01-07
could it be an update failed and that bugged your system for continuous restart? or it is a kernel bug - try another kernel version to see if that fixes your problem.

Also, if none of the above caused it consider making a reinstall of ubuntu.

Regards

---

### Post by qsebas on 2012-01-07
how do I try another kernel version?

---

### Post by blackbird34 on 2012-01-07
If you've had an Ubuntu install for a while, you may have had a few kernel updates. You can revert to a previous kernel in the GRUB boot menu, it may be hidden under "previous Ubuntu versions" or something like that.

Attached is a screenshot of mine showing how you can check in Synaptic Package Manager which kernel(s) you have, the ones with a green square. I have the 2.6.38-11 , 2.6.38-12 and 2.6.38-13 kernels installed (Ubuntu 11.04).

If you don't have Synaptic, you can get it in the Software Center.

---

### Post by qsebas on 2012-01-07
is there a way to track who triggered the shutdown?

---

### Post by dino99 on 2012-01-07
> **qsebas said:**
> is there a way to track who triggered the shutdown?

of course, watch the logs: /var/log/ and .xsession-errors

like your room, your distro needs some maintenance to run smootly

---

### Post by Cosme on 2012-02-10
Hello! I have the same problem than QSebas. I have a vanilla Ubuntu 11.10 (as it gets installed from the DVD) no problem with that until I installed the last udates a few days ago, and now I have the same rebooting problem. In my case it doesn't wait the 60 seconds, it says that the system needs to reboot and 2 seconds after that it shut down the notebook (LG 550).
It happens 10 minutes after I start any video online, at youtube for example. It could be a flash related issue?

> 
of course, watch the logs: /var/log/ and .xsession-errors

I dindn't find anithing in those logs that could indicate a request of shut down the machine.

Thank you in advance :)

---

