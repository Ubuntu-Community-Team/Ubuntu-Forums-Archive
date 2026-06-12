---
title: "intel-xorg"
date: 2010-05-23
forum: General Help
---

### Post by nexoncore on 2010-05-23
How can I upgrade to the latest stable or unstable intel-xorg driver.?

**Problem**
The current driver only allows to a 1300 x something resolution, where as my monitor's native one is 1920 x 1080. When I boot up to window's this works fine, but in Linux I don't get the proper resolution or anywhere near.

I have modified my xorg before, and achieved the desired resolution, but lost all effects, problems I had with the full resolution were
- Severe Video tearing
- No Effects
- Online Video Blanked when Full
- Loss of window's borders unless no effects was forced

At the same time, I cant stick at the lower resolution which eliminates the problems above as it hurts my eyes and does not do justice to this monitor.

The Graphics I am using are embedded intel accelerated graphics G41 embeded on a brand new Gigabyte EnergySaver motherboard.

---

### Post by nexoncore on 2010-05-23
Anyone?

---

### Post by nexoncore on 2010-05-23
Anyone? I may have forgotten to mention I am running ubuntu 10.04

---

### Post by nexoncore on 2010-05-23
Anyone, I really dont want to have to ditch ubuntu and go back to M$

---

### Post by Macchi on 2010-05-23
Dear nexoncore, 
Sorry I don't have a solution for you but I noticed your thread since I am also having problems with intel graphics on Ubuntu 10.04.
 
Please have some patience and eventually you will receive good hints from this community. I understand your frustration, but you may have to allow more time for your request to be read by several people, before a possible solution arrives. Only a couple of hours on a sunday evening is not enough for reaching a large group that may give you suggestions.

I have had slightly large screens working fine with intel graphics on earlier versions of Ubuntu. By the way, since the release candidate for Lucid Lynx was released, kernels higher than 2.6.32-19 crash on one of my systems with Intel 85X graphics.



Is your monitor recognized when you go to System->Preferences->Monitors?

---

### Post by nexoncore on 2010-05-23
No its not recognised by model, either make. In regards to the replies I have been doing is due to past experience with these forums. I have had problems before and they had never got a single reply, hence why with more recent ones I have bumped them up so they are at least on a viewable page.

---

### Post by lykwydchykyn on 2010-05-23
About the only way I know of to get a newer intel driver is to update your kernel and xorg, since the driver is open source.

You can try adding the xorg-edgers ppa to get a bleeding-edge version of xorg, and maybe the kernel-ppa to get the latest kernel.  Be aware that if you're using any proprietary wireless, sound, or other drivers they may not work with a newer kernel.  Also be aware that this may impact the stability of your system.

Kernel ppa:  [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)
xorg edgers: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Macchi on 2010-05-24
nexoncore, the resolution that you have mentioned is far from unusual, thus a solution must be possible! Some older Intel graphics managers had very limited memory and could not work in higher resolutions. But this might not be the case, since you have reported that you system configuration works fine with Windows.

Do you get any references from Google on similar problems for your motherboard model or monitor with Linux or Ubuntu?

As a reference you may check this:
[http://intellinuxgraphics.org/user.html](http://intellinuxgraphics.org/user.html)





PS:
> **lykwydchykyn said:**
> About the only way I know of to get a newer intel driver is to update your kernel and xorg
...(stuff deleted)

Yes, there might be several workarounds, and updating the kernel leads you, so to say, to the kernel of the issue. Hopefully the latest kernel version is better at handling functionality than earlier versions. That is true as long as regression errors do not take over.

My unfortunate current experience is that kernel updates are heaven and hell, since "new" devices are added, but a lot of "older" functionality has started to break. Right now these two time windows have touched each other, and among a dozen test machines I have no systems that work without problems. This prevents me completely from being able to recommend GUN/Linux and Ubuntu to several business enterprise clients.

---

### Post by nexoncore on 2010-05-24
I cant really find anything regarding my motherboard and linux. The motherboard I am using is a GigaByte G41M-ES2L.


Is it possible that an older version of ubuntu would have better support for my graphics, such as 9.10?

---

### Post by Grenage on 2010-05-24
Hi there,

The tearing you reported with a custom xorg.conf, was that recent?  I have a rough guide [here]("http://www.grenage.com/xorg.html").

---

### Post by nexoncore on 2010-05-24
I used that before, it didnt really stop the tearing but did reduce it somewhat. But video's from web blanked at full screen and I was forced to have no effects meaning no docky ect.

Your guide was good for forcing the desired resolution, but issues with intel-xorg ****ed everything up apart from the resolution. But thank's for your help with that, it was very helpful at the time.

---

### Post by Grenage on 2010-05-24
This is real 'clutching at straws' stuff, but does it help if you add:

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Does it improve at all?

---

### Post by nexoncore on 2010-05-24
Nope sadly

---

### Post by Grenage on 2010-05-24
Unfortunately, I'm out of suggestions; I am guessing that the Linux driver is struggling with such a high resolution +effects.  Hopefully someone else will chime in.

---

### Post by nexoncore on 2010-05-24
Thanks for your help anyway, im considoring trying an earlier version of ubuntu, seeing how it copes with an earlier kernel version

---

### Post by Grenage on 2010-05-24
Some people have reverted to earlier revisions, but I've never done it myself and I've no Intel board to test in on:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by nexoncore on 2010-05-25
Anyone else have suggestions?

---

### Post by Macchi on 2010-05-25
Are there any shared memory settings on the BIOS? Some controllers have customizable limits on the amount of shared memory that may interfere with larger screens and graphic effects.

By the way, it is easy to test a system with live distros, preferably on USB or on CDs. I would try something in the range from 8.04 to 9.10. 






PS: I am sorry for such troubles around Ubuntu because most mortal users don't have neither the time nor the skills to deal with advanced hardware issues. At the same time is it a pity that many leading hardware manufacturers do not actively promote linux drivers. It is sad that the popular Intel 85X & 91X etc graphic managers are still unstable with the most recent Ubuntu kernels for 10.04 LTS. In our case this is among the key factors preventing a whole manufacturing industry with 30 users and 40 machines from entering GNU/Linux.

---

