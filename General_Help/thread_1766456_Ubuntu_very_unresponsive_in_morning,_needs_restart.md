---
title: "Ubuntu very unresponsive in morning, needs restart"
date: 2011-05-24
forum: General Help
---

### Post by mbeeby on 2011-05-24
Since upgrading to 11.04, I've been coming into work in the mornings to find ubuntu extremely unresponsive, and requiring that I restart the computer. 

In many cases, I didn't leave a task running overnight. After a few seconds I can enter "top" into a terminal, but I don't see any tasks consuming memory or cpu time.

Any ideas how I can track down the cause of this problem?

Thanks!

-Morgan

---

### Post by mbeeby on 2011-05-27
bump

---

### Post by wildmanne39 on 2011-05-27
> **mbeeby said:**
> bump
Hi, I have seen a lot of problems like this one on here but I have not seen an answer. I need to know what the specs of your system are? Have you enabled the cube or desktop effects? What video card do you have did you activate restricted drivers?If so from where? Also you can log out and click on your user name then go to the bottom of the screen and click on ubuntu classic with no effects and see if that fixes it.

---

### Post by mbeeby on 2011-06-01
Hi,

Thanks for the response!

I'm running on a 64 bit Dell with an Nvidia FX1700 Quadro card with NVidia's drivers. No cube or desktop effects. I can't log out -- it hangs in the process, so I have to shutdown, then turn it on again.

Any idea what logs or programs I could use to attempt to troubleshoot the source of the problem?

Thanks!

---

### Post by mbeeby on 2011-06-16
bump...

No-one has any tips for troubleshooting a very unresponsive machine?

---

### Post by Synoc on 2011-06-16
> **mbeeby said:**
> bump...

No-one has any tips for troubleshooting a very unresponsive machine?

I am unresponsive in the morning too. so I sympathize with your computer's problem of having a slave driver for a boss. I don't know if this will help, but try to pull up a top and see if there are any zombie programs, and a ps -A to find any programs that could bee running you didn't start. leaving an unattended PC running all night is a bad practice, unless you need it running. it's unlikely someone is playing with your computer. but zombie programs... that happens more frequently than I care for. it could be a program you closed out the night before that didn't close and it is using processor power to try and shut down it's just not managing it. logging off or shutting down could take longer under those circumstances.

---

### Post by holycow131415 on 2011-06-16
Upgrading can cause problems... I would suggest backing up your data so that you can do a clean install of 11.04, or just go back to 10.10. When I say clean install, I mean reformatting the partition Ubuntu is on. So if you dont already have a CD, download the ISO and burn it to a disk so that you can boot off it.

---

### Post by Duncan Williams on 2011-06-16
You could try running bleachbit in the morning.

[http://bleachbit.sourceforge.net/features](http://bleachbit.sourceforge.net/features)

(available in software-manager)

---

