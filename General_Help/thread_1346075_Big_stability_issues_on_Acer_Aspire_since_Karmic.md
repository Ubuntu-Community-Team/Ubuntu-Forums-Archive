---
title: "Big stability issues on Acer Aspire since Karmic"
date: 2009-12-04
forum: General Help
---

### Post by Rackstar on 2009-12-04
Hi,

Thanks for everyone starting to read this, because I know this isn't a very appealing threadtitle, as it isn't a specific problem. I need help pinpointing the actual problem on my laptop.

I did several reinstalls of 9.10, I had a stable Jaunty.

Things I encounter:
- Something during boot sometimes fails, leading to a freezing gdm right after logging in. Maybe due to gnome-panel not fully loading. I reported this here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/344428](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/344428)
(No, when I'm not able to start a normal gnome-session, I also can't start an xterm session)
- Suspend and resume works, but my system becomes unstable. Sometimes gnome-power-manager applet is gone, sometimes network manager applet freezes. gnome-terminal freezes. I used to have a kernel oops when resuming, but this seems to have been fixed since a couple of weeks, as reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417842)
- Sometimes my screen goes black, I have to press a key to light up my screen again and I have an icon in my tray, it had a text, redirecting me to this website: [gnome-power-manager and blanking (removal of bodges)]("http://blogs.gnome.org/hughsie/2009/08/17/gnome-power-manager-and-blanking-removal-of-bodges/")
- Update manager fails, when my system is unstable. It starts unpacking things, and when configuring or updating man-db, it freezes. Probably the same thing as gnome-terminal freezing, as reported above.

Previously, somebody noticed errors about acpi in my logs. I'm not an expert enough to understand a lot of this. But acpi has to do with hardware (optimizations?), so it is probably hardware related.

There might be more things, but I forgot. I have done a lot of research, and tried reporting everything. But no success yet. I would really love to help fixing this, as I want it fixed before Lucid. But eventually I'll have to return to Jaunty, probably...

Please, if somebody could point me into the right direction, please do.

Any help would hugely be appreciated. Thanks!

---

### Post by Rackstar on 2009-12-05
Bump

---

### Post by teh603 on 2009-12-09
I'd suggest just going back to Jaunty. I don't think the stability issues are likely to get dealt with before Lucid. At least one of them was given low priority in Launchpad.

---

### Post by sedawk on 2009-12-09
Do you have any issues with the LiveCDs, e.g. does
Jaunty work while you experience (random) crashes with Karmic?

Search the web for "linux" and your model number to find
other people using the same (or a similar) hardware platform.

There are sites like "linux on laptop" or "mobile tux" where
people publish their experience with linux on their hardware.

---

### Post by Rackstar on 2009-12-12
Hey,

I had trouble with live CD's of Karmic. Jaunty is rock stable. I downgraded this morning..

Feels like a big step backwards, I really hope Lucid will fix my problems. I don't understand why I seem to be the only one having this problem. And as not a lot of people have this problem, the chance of it being fixed is getting smaller.

---

### Post by wilee-nilee on 2009-12-12
> **Rackstar said:**
> Hey,

I had trouble with live CD's of Karmic. Jaunty is rock stable. I downgraded this morning..

Feels like a big step backwards, I really hope Lucid will fix my problems. I don't understand why I seem to be the only one having this problem. And as not a lot of people have this problem, the chance of it being fixed is getting smaller.

Did you do all the reinstalls with the same download or thumb? My acer aspire one has had no real problems but we may have some different hardware.

---

### Post by Rackstar on 2009-12-12
Hey, thanks for your answer.

I did the installs with multiple 64bit and 32 cds/usbs. It took a while before any could install right, this should've been a sign for me back then :)

It's probably the same why I could boot my computer only 30% of the time.

---

### Post by wilee-nilee on 2009-12-12
> **Rackstar said:**
> Hey, thanks for your answer.

I did the installs with multiple 64bit and 32 cds/usbs. It took a while before any could install right, this should've been a sign for me back then :)

It's probably the same why I could boot my computer only 30% of the time.

Yeah my installs are at the most 20 minutes, glad you have Jaunty running though it is a good distro.

I just did a full install of Lucid on a 16 gig thumb using about 6 gigs and it looks pretty good and runs fast. If you have a big enough thumb like a 8 gig one you could do the same but point the bootloader to the thumb or you will have a unbootable computer. You could also use the USB creator to load the ISO onto a thumb and set the persistent big enough and it will save the updates and installs. I have done this it boots up slower but runs about as fast as the distro installed.

---

### Post by judge jankum on 2009-12-12
I can't run 9.10 but Jaunty runs great on the 4 puters I have it on, Anything that works is a step forward" Just wish it could be LTS....

---

### Post by wangsuda on 2009-12-12
What model Acer Aspire are you using? And what kind of hardware? I, too, use an Acer Aspire (4730z) and to get Karmic perfect, I did have to do some slight tweaking (not much). Perhaps I can help if I know more about your hardware.

---

### Post by pedja_portugalac on 2009-12-12
> **Rackstar said:**
> Hey,

I had trouble with live CD's of Karmic. Jaunty is rock stable. I downgraded this morning..

Feels like a big step backwards, I really hope Lucid will fix my problems. I don't understand why I seem to be the only one having this problem. And as not a lot of people have this problem, the chance of it being fixed is getting smaller.
My laptop is an Acer Aspire 8920G and I also have some problems you already mention here. First problem was installing from alternate CD and choosing encrypted LVM. It freezes forever by the end 96%, writing user informations and passwords. It will install right if I choose not to encrypt HDD nor home dir. Second problem was mounting sometimes some disks during boot. Apart this, everything seemed to work good. For the first time I get surround sound out of the box without much tweeking. But since, 3 days ago, sometimes I have problems loading googles web page and playing youtube videos in firefox as well as in Chrome and I don't think it have anything to do with Ubuntu nor Firefox. I agree with you that Jaunty was rock stable even on my laptop but Karmic brought bunch of new features to it. Ones ext4 file system and Grub 2 will became stable it will rock more then Jaunty does. Keep on testing and feeding bug reports, hopefully soon we'll resolve some of them.

---

### Post by Rackstar on 2009-12-12
Hey,

And thanks for the replies!

My hardware is an Acer Aspire 9420 (Nvidia Geforce Go 7300). 

As this is my main computer, I won't install Lucid yet (it's only in alpha 1 right now, breakage to come!). However, I will test if the problem still exists at beta.

---

### Post by wangsuda on 2009-12-13
> **Rackstar said:**
> Hey,
My hardware is an Acer Aspire 9420 (Nvidia Geforce Go 7300). 


Sorry, I don't know enough about Nvidia cards to help. I run an Intel card.

---

### Post by mikitz on 2010-04-03
I am having the same issue after updating from Karmic to Lucid Beta 1 on Acer Aspire One. However Karmic was working fine.

---

### Post by Rackstar on 2010-04-03
> **mikitz said:**
> I am having the same issue after updating from Karmic to Lucid Beta 1 on Acer Aspire One. However Karmic was working fine.

Strange, because I had trouble in Karmic, but most things are solved in Lucid for me..

Only some hard lockups sometimes, (not unusual in this stage), and lack of suspend/resume. (which did work in alpha 3 Lucid)

Sorry to hear this. Try to file a bug report. It's still in beta 1, there is chance that'll be fixed.

---

### Post by mikitz on 2010-04-03
The Lucid live distro works wonderfully. I upgraded from Karmic to Lucid and just get the command line login screen. I have run update and upgrade from aptitude several times now to no avail..

---

