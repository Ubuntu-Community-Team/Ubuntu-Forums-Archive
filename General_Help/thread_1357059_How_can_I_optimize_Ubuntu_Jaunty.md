---
title: "How can I optimize Ubuntu Jaunty?"
date: 2009-12-16
forum: General Help
---

### Post by Puzzled Guy on 2009-12-16
Hi Guys.

I installed Jaunty about a month back. It was quite fast then but seems to be slowing down now (actually, it IS slowing down).

Any tips on speeding it up? By speeding up I mean speeding up everything and anything that can be sped up.

Please? I really need to squeeze some speed from this machine. Last time I checked, it took 1 minute and 11 seconds to boot from a cold start to the GNOME Desktop, and that is with zero seconds GRUB timeout and automatic login.

My goal is to get it as fast as possible without actually getting a better computer.

**My computer specs are:**
Model: MSi Wind U100
OS: Ubuntu 9.04 Jaunty Jackalope
Display size: 10 inches
CPU: 1.6 GHz Intel Atom
Memory: 2 GB
Available Disk Space: 127.8 GB
Graphics: Intel GMA 950

By the above info you can tell that I don't exactly have a supercomputer.

I'm desparate. If this just gets slower, it won't be any better than Windoze.

Plus, can I have some newbie (noobie?) step-by-step instructions?


3 Cheers for anyone who can help a friend in need:guitar:

---

### Post by scouser73 on 2009-12-16
Check this How To for speeding up the boot process. [[COLOR="Red"]**Speed Up Ubuntu Boot Process**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491")

Go to **Synaptic Package Manager** and search for and install **BleachBit** will remove cached websites and more.

---

### Post by Puzzled Guy on 2009-12-16
Thanks for the link, scouser73.

But there is a part in it that I don't understand:

```
III. Alter the /etc/inittab file
     Code:
     vi /etc/inittab 
then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.
```I searched before editing it and it didn't exist. Zip, nothing.

How do I continue then? Create the file myself? But the above instruction implies that there already is something in it.

Is there an alternative for this instruction?

---

### Post by Puzzled Guy on 2009-12-17
Bump

---

### Post by Puzzled Guy on 2009-12-17
I did what the thread said (minus the part about the inittab file) and then did a cold reboot.

It didn't get any faster. About the same as before.

Any other tips?

---

### Post by realzippy on 2009-12-17
> **Puzzled Guy said:**
> Thanks for the link, scouser73.

But there is a part in it that I don't understand:

```
III. Alter the /etc/inittab file
     Code:
     vi /etc/inittab 
then comment out tty4,tty5, and tty6. Just leave tty1, tty2, and tty3. Three vts should be enough for a laptop or desktop user. Save the file.
```I searched before editing it and it didn't exist. Zip, nothing.

How do I continue then? Create the file myself? But the above instruction implies that there already is something in it.

Is there an alternative for this instruction?


The HowTo is pretty old.The /etc/inittab does not exist anymore,things have changed.Beware of old Howtos...

BTW,fast bootup has nothing to do with a fast system...

---

### Post by Zlatan on 2009-12-17
> **Puzzled Guy said:**
> Hi Guys.

I installed Jaunty about a month back. It was quite fast then but seems to be slowing down now (actually, it IS slowing down).

Any tips on speeding it up? By speeding up I mean speeding up everything and anything that can be sped up.

Please? I really need to squeeze some speed from this machine. Last time I checked, it took 1 minute and 11 seconds to boot from a cold start to the GNOME Desktop, and that is with zero seconds GRUB timeout and automatic login.

My goal is to get it as fast as possible without actually getting a better computer.

**My computer specs are:**
Model: MSi Wind U100
OS: Ubuntu 9.04 Jaunty Jackalope
Display size: 10 inches
CPU: 1.6 GHz Intel Atom
Memory: 2 GB
Available Disk Space: 127.8 GB
Graphics: Intel GMA 950

By the above info you can tell that I don't exactly have a supercomputer.

I'm desparate. If this just gets slower, it won't be any better than Windoze.

Plus, can I have some newbie (noobie?) step-by-step instructions?


3 Cheers for anyone who can help a friend in need:guitar:

Hi, if I were you, I would try following (usually helps me):
1. install Karmic (latest Ubuntu)
2. use lighter programs than Ubuntu default: Epiphany instead Firefox, Abiword, Gnumeric instead Open Office Write and Calc
3. disable unnecessary proceses
You can find plenty of infos and how-tos on these topics in this forum:) Good luck:)

---

### Post by realzippy on 2009-12-17
There is an Ubuntu for Intel Atom CPUs...  :

[http://www.cyberciti.biz/tips/ubuntu-linux-remix.html](http://www.cyberciti.biz/tips/ubuntu-linux-remix.html)

---

### Post by Puzzled Guy on 2009-12-17
My ubuntu already is a netbook remix. Oh, by the way, I installed bootchart. Does anyone know how to read this thing and tell me what to do to speed it up a little?

Thanks.

---

### Post by Puzzled Guy on 2009-12-17
> **Zlatan said:**
> Hi, if I were you, I would try following (usually helps me):
_***1. install Karmic (latest Ubuntu)***_
2. use lighter programs than Ubuntu default: Epiphany instead Firefox, Abiword, Gnumeric instead Open Office Write and Calc
3. disable unnecessary proceses
You can find plenty of infos and how-tos on these topics in this forum:) Good luck:)

Problem is, the computer I have has a lot of bugs with Karmic and it is not recommended to upgrade yet (that's what the hardware compatibility list said)

---

### Post by Puzzled Guy on 2009-12-17
> **Zlatan said:**
> Hi, if I were you, I would try following (usually helps me):
_***1. install Karmic (latest Ubuntu)***_
2. use lighter programs than Ubuntu default: Epiphany instead Firefox, Abiword, Gnumeric instead Open Office Write and Calc
3. disable unnecessary proceses
You can find plenty of infos and how-tos on these topics in this forum:) Good luck:)

Problem is, the computer I have has a lot of bugs with Karmic and it is not recommended to upgrade yet (that's what the hardware compatibility list said)

But the other stuff looks pretty good. I'll try them

---

### Post by SnappyU on 2009-12-17
For him using the MSI Wind u100, he should **not** be installing Karmic, at least not till the bugs are fixed.

Read the release notes about it.
1. Brightness bug
2. USB bug (thumbdrive etc not working)

I tried it myself, failed miserably ... and downgraded back to 9.04.  Upside being that I have my home directory on a separate partition, so it was fairly easy to reinstall.

> **Zlatan said:**
> Hi, if I were you, I would try following (usually helps me):
1. install Karmic (latest Ubuntu)
2. use lighter programs than Ubuntu default: Epiphany instead Firefox, Abiword, Gnumeric instead Open Office Write and Calc
3. disable unnecessary proceses
You can find plenty of infos and how-tos on these topics in this forum:) Good luck:)

---

### Post by Puzzled Guy on 2009-12-18
Bump

---

### Post by Ibidem on 2010-01-04
Hello,
I'm using the Kuki Linux remix (actually, NOT QUITE...), with 1 minute from power on to usable desktop on an Acer Aspire One (15-20 seconds in BIOS).
Here are a few tips:
1. Install Netbook kernel
Such as [sickboy]("http://www.aspireonekernel.com/") 2.6.29/ the [Kuki Linux kernel]("http://www.kuki.me/downloads/") 2.6.31 (both Aspire One targeted, may work w/ MSI Wind) or the [Array netbook kernel]("http://array.org/ubuntu/") 2.6.28 (use the "netbook" kernel, the other is eeepc specific).
2. Get rid of GNOME!
Gnome takes a lot of time starting and running... If you're _really_ serious, try using OpenBox for its instant "there"--if it's usable for you (hint: right click==menu); IceWM works better for me (looks like Windows 9x/2k/XP if you don't play around much) and takes 3 seconds to load; Xfce or LXDE is my third suggestion.
Some folks use gnome-core, but I don't know what you need to lose to get there.
3. Remove usplash --maybe not that significant, but it sure is less boring to watch the boot scripts scroll by... :-)
4. Do you need printing? bluetooth?  If not, I would uninstall these...
5. Try using bum (Boot-Up Manager) to configure services.  The method in the old howto is out-of-date, but not the services.
Eeebuntu.org has some tips on speeding up FireFox; make sure to use firefox 3.5 (Mozilla may be better than repositories) or another browser--3.0 is slow (~5 sec mozilla.org page load  in 3.0 vs ~2 sec in 3.5)
If you use a lightweight WM to replace GNOME, install "menu"
Replace Nautilus with pcmanfm (or Thunar or the like, with LXDE/Xfce).

If you're really serious, replace GDM with Slim (after reading up); or just replace Ubuntu with Arch, AntiX, TinyCore Linux, Puppy Linux, or some other fast distro; Ubuntu may beat Windows, but it's always been among the slower distros of linux.
My own system could be roughly duplicated by;
apt-get install icewm grun
apt-get install menu
apt-get install pcmanfm roxterm vim-gtk
apt-get install firefox3.5
Hope this helps,
Ibidem

---

