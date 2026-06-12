---
title: "Can't get newest real time kernel to show up in Grub 2 (Ubuntu Karmic)"
date: 2010-04-26
forum: General Help
---

### Post by indstr on 2010-04-26
I want to try out the realtime kernel to get my audio latency down. I have installed the realtime kernel packages according to the Ubuntu Studio preparation documentation here - [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation). I have also run sudo update-grub


However, when I boot up, the realtime kernel option does not show up in grub2. The current kernel I am using is 2.6.31-17, but the only options in grub for it are -386 and -generic. 

There is a previous entry of 2.6.31-9-rt which I had attempted to use previously (sometime last year) but if I select it, it doesn't even boot at all.

I checked my /boot directory and there is no vmlinuz-2.6.31-17-rt file ....  Which I am assuming is why it doesn't show up or add when I run update-grub ...  

But I am currently at a loss for how to actually get the 2.6.31-17 realtime kernel file and add it to grub2.

Any help is appreciated. Thanks

---

### Post by rnerwein on 2010-04-26
hi
why to shoot with tanks to little birds.
have a look at:
taskset - retrieve or set a process's CPU affinity
cpuset - confine processes to processor and memory node subsets
chrt    - manipulate real-time attributes of a process
think this still stuff will help you even with the default kernel.

have fun
ciao

---

### Post by indstr on 2010-04-26
I tried "completely removing" the linux-rt and linux-headers-rt libraries in synaptic. Then updating everything automatically. Then pulling up linux-rt and linux-headers-rt again in synaptic... They are still showing version 2.6.31-9-rt.

What is going on?

---

### Post by indstr on 2010-04-26
This is crazy. I reinstalled the linux-rt and linux-headers-rt libraries which created a new kernel, but it was based off 2.6.31-9 again. I don't know how to make it newer! It actually boots into it now too and I'm assuming it's realtime, except my ALSA is not working because I can't find a backport of alsa-modules back to 2.6.31-9 (only back to about -13) ...
Please somebody tell me how to install a newer version of the rt kernel!

---

