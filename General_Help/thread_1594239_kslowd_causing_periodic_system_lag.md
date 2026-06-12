---
title: "kslowd causing periodic system lag"
date: 2010-10-12
forum: General Help
---

### Post by vckeating on 2010-10-12
I just upgraded to 10.10 and am finding that the processes kslowd00* seem to be generating a great deal of lag when they run about every 15-20 seconds.  It is affecting mouse movement, which stutters, and typing, which causes errors in the document - primarily missing letters.  

Is there any known fix to this problem?

---

### Post by jseethr on 2010-10-16
Same problem here since updating to 10.10.

Maybe those with the problem should say something about their hardware.

I have a Dell Latitude D505 which runs a 1.5 GHz Pentium M processor. /proc/cpuinfo says it's CPU family 6, model 9.
My graphics card is an 855GM from intel which already caused lots of problems, maybe it is involved here, too.

Please post any news if you something on this topic.

---

### Post by htrp on 2010-10-17
Hi!
I also had this problem. Accordning to:
[https://bbs.archlinux.org/viewtopic.php?id=105113](https://bbs.archlinux.org/viewtopic.php?id=105113)
it is kernel related. I downgraded to kernelversion 2.6.32-25, and the problem disappeared.

/Tomas Persson

---

### Post by vginders on 2010-10-19
I experience the same problem anf filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661012]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/661012")

May I suggest you confirm info about your problem and your hardware over there? Please note that you can easily do that with the command:

> apport-collect 661012

---

### Post by htrp on 2010-10-21
"apport-collect 661012" does not seem to work: 

''You are not the reporter or subscriber of this problem report, or the report is a duplicate or already closed.

Please create a new report using "apport-bug".''

---

### Post by ridgeland on 2010-10-21
I just installed Ubuntu 10.10 on a Gateway 4024 Laptop.  lshw shows it has:
display: VGA compatible, product: 82582/855GM Integrated Graphics Device

With the fresh install of Ubuntu 10.10 I get kernel 2.6.35-22 This gives me the kslowd00x problem.

So I downloaded and tried a 2.6.34 and a 2.6.36 kernel.
Here is my comparison using top.  I booted each kernel, opened a terminal window ran top and left it running for 15 minutes.  Here are the loads:
2.6.35-22 - - - - uptime 15 min - load average 0.66 0.60 0.46
2.6.34-02063401 - uptime 15 min - load average 0.00 0.02 0.04
2.6.36-020636 - - uptime 15 min - load average 0.14 0.25 0.18

So I'm sticking with the "34" kernel.

Here is how I installed the kernels:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
then I chose  v2.6.34.1-maverick/
then download three kernel packages
linux-headers-2.6.34-02063401-generic_2.6.34-02063401_i386.deb
linux-headers-2.6.34-02063401_2.6.34-02063401_all.deb
linux-image-2.6.34-02063401-generic_2.6.34-02063401_i386.deb
to somewhere/  (somewhere where there are no other linux* files)
I followed
[http://thanhsiang.org/faqing/node/129](http://thanhsiang.org/faqing/node/129)
Then open a terminal window
$ sudo su
# cd somewhere/
# dpkg -i linux-*
I'm still working on the hold part...
reboot
GRUB will list highest kernel first so arrow down to get to "34".
I get a side effect.  Now when it boots it complains of a low memory error.  It didn't before and doesn't with kernel 35.

---

### Post by James78 on 2010-10-21
So this is what's causing my system slow down and stuttery mouse! Ugh!

---

### Post by ridgeland on 2010-10-21
OK so here's how I locked the version
> In Synaptic Package Manager, search for the software that you don't want to be upgraded, select it & go to Package & then check the box Lock Version
The color scheme was yuck so I changed it with Settings -> Preferences -> "Colors" tab then to a lighter red so I could read it.
Thank you to
[http://ubuntuforums.org/showthread.php?t=1321582](http://ubuntuforums.org/showthread.php?t=1321582)
Post #4 - scouser73

I'm hoping that locking the version also stops the auto overwrite of /boot/grub/grub.cfg.  I edit it like I want it.

---

### Post by ridgeland on 2010-10-27
This is interesting.
[http://linux.derkeiler.com/Mailing-Lists/Kernel/2010-06/msg05199.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2010-06/msg05199.html)
Theodore Ts'o was asking why kslowd was eating 16% of his CPU.
He started asking in June when he updated to Ubuntu Lucid - kernel 2.6.35-rc2

---

### Post by gator on 2010-10-29
We have a squid server running maverick. Slow ssh logins and top showing kslowd001 interrupting work. I believe the server is a IBM X306m but i may be wrong. Our other IBM squid server works fine.

---

### Post by James78 on 2010-10-29
My server sometimes has slow SSH logins, and slow sessions (e.g. stuttering text entry). I don't know if it's related to this, but it's very possible, especially when I checked top.

---

### Post by aezren on 2010-10-30
I have the same kslowd000 issue as well. I have several processes keep running kslowd000, kslowd001, kslow002, etc... I have same symptoms as everyone else. Sluggish mouse, stuttering mp3 playback, etc. I am thinking about the kernel downgrade, just have not had time to try it yet. I am running 64 bit Maverick kernel 2.6.35-22-generic. I have a Lenovo T400 laptop. I'll have to do something soon. This is starting to really get annoying :(

---

### Post by aezren on 2010-10-30
found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662946)

I installed the kernel 2.6.36 as recommended and so far so good. I'll try it out for a while and let you know how it goes.

---

### Post by James78 on 2010-11-02
Edit:: Using 2.6.36 kernel right now. There's still some slowdown, but it's greatly decreased compared to the last kernel. It's much better, so I'm still happy.

Current links to AMD64 packages as of this posting date:

linux-headers-2.6.36-1_2.6.36-1.7_all.deb
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.36-1_2.6.36-1.7_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.36-1_2.6.36-1.7_all.deb)

linux-headers-2.6.36-1-generic_2.6.36-1.7_amd64.deb
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.36-1-generic_2.6.36-1.7_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.36-1-generic_2.6.36-1.7_amd64.deb)

linux-image-2.6.36-1-generic_2.6.36-1.7_amd64.deb
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.36-1-generic_2.6.36-1.7_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.36-1-generic_2.6.36-1.7_amd64.deb)

For the ones that say amd64 on the end, replace with i386 for x86 versions.

---

### Post by aezren on 2010-11-02
So I have been running the 2.6.36-1-generic for a few days now. Seems better, not perfect, but much better. Problem is since upgrading the kernel my laptop battery will no longer give an estimate of time remaining. It just says (estimating...)

I noticed when i installed it is said it was geared toward desktop systems. I looked at all of the kernels available and this seemed like the best 64 bit choice for my Lenovo T400. Any ideas how to fix the time estimate?

---

### Post by James78 on 2010-11-02
Other than downgrading, no idea. The newer kernels graphics drivers cause screen tearing for me, either that, or it's Xorg (don't Xorg drivers compile as modules into the kernel? That'd mean it's still Xorg in that case), where 10.04 was fine. Frustrating...

Edit:: After some testing, it appears it might be related to KDE graphics effects.

---

### Post by ageyfman on 2011-01-02
I had this issue with 10.10, on a Core2Duo machine, headless, running Maverick Server, and I think I just fixed it by upgrading to a new kernel. The new kernel I went to was 2.6.37-11.

I was seeing this issue after about 5 mins of uptime. Every time. My load avg would go up and up, until it reached about 20, at which point I could no longer SSH into the machine, or really do anything at all.

I tried both to upgrade from 2.6.35-22 to 2.6.35-24 and to 2.6.37-11. The 35-24 upgrade did not work. I would continue getting the kslowd000 and kslowd001 (001 especially) taking up 100% of CPU (Core 2 Duo DESKTOP, not laptop, headless).

So, I installed the Lucid Kernel PPA:
```

sudo add-apt-repository ppa:kernel-ppa/ppa

```
then installed the new kernel headers and image
```

sudo apt-get install linux-headers-2.6.37-11 linux-image-2.6.37-11

```
then reboot
```

sudo reboot

```

after 20 mins of uptime, I am not seeing the kslowd001 process taking up any noticeable CPU.

---

### Post by aezren on 2011-01-02
I was able to solve this a few weeks ago as well. I upgraded to kernel 2.6.36.2 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36.2-natty/")

I tried a version of 2.6.37.x RC and had issues shutting down properly so I install the latest non RC version. At that time it was 2.6.36.2

After upgrading I would still have minor mouse lag every once in a while. To fix this I disabled polling of the drm_kms_helper and have not had an issues since.

```
sudo -i
echo "options drm_kms_helper poll=N">/etc/modprobe.d/local.conf
reboot
```

After upgrading to the newer generic kernel my laptop battery indicator would no longer work. It would not tell me how much time or percentage was left on the battery. To fix this I install IBAM and vubat. This works much better than the standard gnome battery indicator ever did. It is a very reliable battery indicator. The gnome indicator time was always all over the place anyway.

---

### Post by noxan on 2011-01-14
I have the problems (a process named **kslowd002 **appears with up to 5% cpu usage while my mouse pointer and the music playback stop for less than a second), but only if i plug in my external monitor via HDMI - if i unplug it, everything works fine again (no matter if the monitor is enabled in ubuntu or not).

I am running ubuntu10.04LTS (2.6.32-27) at the moment with enabled nvidia driver and had the same problems with a ubuntu10.10 installation and clean live-sytem.

edit:
updated to the version [aezren]("http://ubuntuforums.org/member.php?u=1176841") linked and "disabled polling of the drm_kms_helper": works fine as long as i don't plug in my monitor ... :/
if i plug in my monitor again there isn't a kslowd002 process anymore, but the short lag of my mouse pointer still exists...?

---

### Post by mal205 on 2011-02-13
I've had this problem on a Lenovo T400. I tried turning the polling off, with no success. Finally I loaded Kernel 2.6.38-020638rc4-generic. An hour in and it's all looking good.

---

### Post by Smiff2 on 2011-09-21
i notice some kernels are tagged -maverick. but the highest with that tag i can see is .36 - for .37 or .38 is it ok to just install any -natty or -oneiric kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") on 10.10?

edit: there's a [v2.6.37-rc2-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.37-rc2-maverick/") but the question remains, do you need to use a particular kernel built for your ubuntu version, what happens if you install one from a later release like natty?

edit2: think i found my answer here
[http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10](http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10)
[http://ubuntuforums.org/showthread.php?t=1711302](http://ubuntuforums.org/showthread.php?t=1711302)
it is possible to install Natty kernels in Maverick.

i'll see later if this resolves this issue for me.. not sure whether to try .36 or .38 though.

---

