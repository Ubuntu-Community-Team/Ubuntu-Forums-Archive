---
title: "Reinstall XP on partitioned HD? Help/advice please!"
date: 2009-10-23
forum: General Help
---

### Post by aaronchall on 2009-10-23
Greetings!  

My setup: Inspiron 9300, 80GB HD, 2GB RAM, NVIDIA video, and it's 3 years young.  

I need Windows XP for some work things, but it's been acting buggier and buggier, freezing up at the worst times and stuff.  About a month or 2 ago, I partitioned and installed Ubuntu, which I love.  XP is still degrading in performance, even though I uninstalled the antivirus and anything else I can think of to improve its performance.  I'm thinking I just need to reinstall it.  Can I do so without messing up my Ubuntu installation?  Is the point moot because I'd like to upgrade to 9.10 when it's out and fully functional?  

(While I'm on the subject, should I use the dell installation of Ubuntu?  I don't really want to, but if it's measurably better, I suppose I should.  I do have trouble with the audio (the speakers and woofer staying sync'd properly when using the media buttons.))

Thanks!!!

---

### Post by donsy on 2009-10-23
Yes, I would say the point is moot. Wait a week and download the *.iso image of 9.10. Then do a clean install of Windows using the whole disk (you'll be given the option to delete partitions, delete them all). Then proceed with the WindowsXP installation. (Remember, you'll need to install some drivers separately). After the Windows install defrag the ntfs partition and schedule and run a file check. (Make sure you restart Windows to run the file check.)

You can then proceed to install Ubuntu 9.10 as a dual boot, side-by-side with Windows, resizing the ntfs partition like you did before.

---

### Post by donsy on 2009-10-23
Let me emphasize the importance of drivers. The WindowsXP CD does not have drivers for every type of hardware. If your computer came with a separate drivers CD, then no problem. But if not you may have to go to the manufacturers Web site to download them. I found mine on the Dell Web site under downloads.

---

### Post by P4man on 2009-10-23
> **aaronchall said:**
> Greetings!  

My setup: Inspiron 9300, 80GB HD, 2GB RAM, NVIDIA video, and it's 3 years young.  

I need Windows XP for some work things, but it's been acting buggier and buggier, freezing up at the worst times and stuff.  About a month or 2 ago, I partitioned and installed Ubuntu, which I love.  XP is still degrading in performance, even though I uninstalled the antivirus and anything else I can think of to improve its performance.  I'm thinking I just need to reinstall it.  Can I do so without messing up my Ubuntu installation?  Is the point moot because I'd like to upgrade to 9.10 when it's out and fully functional?  

(While I'm on the subject, should I use the dell installation of Ubuntu?  I don't really want to, but if it's measurably better, I suppose I should.  I do have trouble with the audio (the speakers and woofer staying sync'd properly when using the media buttons.))

Thanks!!!

If you reinstall windows, it will overwrite your grub, so youll have to fix that by reinstalling grub (have a livecd at hand). Thats assuming you did a regular install of ubuntu on its own partition. If you did a wubi install from inside windows, then reinstalling windows will trash ubuntu.

As for ubuntu, you can upgrade to 9.10 without reinstalling. Just do the distribution upgrade next week (it will prompt you) to upgrade to 9.10. Not much point in using the Dell cd I guess, though it might be worth checking if Dell actually provides a "Dellisized" 9.10.

---

### Post by aaronchall on 2009-10-24
> **P4man said:**
> If you reinstall windows, it will overwrite your grub, so youll have to fix that by reinstalling grub (have a livecd at hand). Thats assuming you did a regular install of ubuntu on its own partition. If you did a wubi install from inside windows, then reinstalling windows will trash ubuntu.

As for ubuntu, you can upgrade to 9.10 without reinstalling. Just do the distribution upgrade next week (it will prompt you) to upgrade to 9.10. Not much point in using the Dell cd I guess, though it might be worth checking if Dell actually provides a "Dellisized" 9.10.

What if I just format the whole hard drive and run XP from a virtual machine in Ubuntu?  Does the virtual machine do all the .net stuff and everything else Windows and some programs require?

---

### Post by P4man on 2009-10-25
could work. If you got enough ram and your windows apps dont rely on 3d accelleration then  check out virtualbox

---

