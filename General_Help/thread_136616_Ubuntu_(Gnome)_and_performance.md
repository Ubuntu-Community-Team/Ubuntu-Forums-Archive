---
title: "Ubuntu (Gnome) and performance?"
date: 2006-02-26
forum: General Help
---

### Post by Syndrome on 2006-02-26
Hi.

For some time ago, I tried out Ubuntu on a 500Mhz Intel Pentium 3 with 256Mb ram, and had only bad experience. First of all, everything ran very slowly, and second I had problems with the apt-get. But forget that now.

So I decided I wanted to try Ubuntu one more time. I ordered some CDs, and I'll probably get a laptop soon to try it on. The problem? The laptop is at 1.2Ghz, but with only 128mb of ram. I'm afraid that Ubuntu with Gnome may run extremely slow on it. So my question is, did I do anything wrong the first time I tried Ubuntu, or does it work fine on just 128Mb of RAM?

/ syn

---

### Post by Ramses de Norre on 2006-02-26
It will probably work on 128MB, but for best performance you might consider using Xfce instead of Gnome.
I never tried Gnome on a 128MB machine, I'd say try it;)

I know someone using Gnome on a PIII pc, don't know about his frequency or memory but ubuntu runs nice on it with Gnome.. Maybe you had some things badly configured..

---

### Post by Syndrome on 2006-02-26
[QUOTE=Ramses de Norre]It will probably work on 128MB, but for best performance you might consider using Xfce instead of Gnome.
I never tried Gnome on a 128MB machine, I'd say try it;)

I know someone using Gnome on a PIII pc, don't know about his frequency or memory but ubuntu runs nice on it with Gnome.. Maybe you had some things badly configured..[/QUOTE]

Thank you for your answer! :)
Is it hard to uninstall Gnome from Ubuntu and after that install Xfce? Is there any guide?

Badly configured eh? Well, no idea, I didn't configure it at all :)
Just installed and ran it. But anyhow, that doesn't matter right now.

EDIT: Oh, just figured something out. When on a laptop, in windows you can set up som settings for how the computer will behave when closing the lid / flipping down the screen (for example, 'Hibernate'). Is there anything like this in ubuntu, so I can flip down the screen and just turn of the screen to save battery.

---

### Post by antiemptyv on 2006-02-26
Yeah, I just installed Ubuntu on an old 500mhz computer, and Gnome runs really slow on it.  The first thing I did was use apt-get to install Openbox window manager.  Then I can kill Gnome and reboot in Openbox.  Openbox is way lighter and runs surprisingly smooth on the old pc.  There are other light window managers, too.

---

### Post by izmaelis on 2006-02-26
What about replacing Gnome's default Metacity with xfwm4 or openbox? How much faster can a system get after such improvement?

---

### Post by antiemptyv on 2006-02-27
I'm not exactly sure, but replacing metacity with openbox did not improve my performance nearly as much as not using Gnome at all.  I don't know if this is a universal fact, but it was true for me.  Gnome has a lot of apps running behind the scenes, while Openbox--itself being lightweight--runs only minimal programs plus what you want to run.

---

### Post by frodon on 2006-02-27
Gnome developers are working hard on improving performances for the next release of gnome (2.14) which will coming soon, so we have to wait several month ;)

---

### Post by pppetter on 2006-02-27
gnome 2.14 will be shipped with dapper :)

---

### Post by Ramses de Norre on 2006-02-28
To uninstall gnome: sudo apt-get remove ubuntu-desktop
To install Xfce: sudo apt-get install xubuntu-desktop

About the lid: I think it is possible, but I don't know where to configure it (haven't got a laptop myself yet). But I'm sure you can find somethings about it on the forum using the search function.

---

### Post by lapsey on 2006-02-28
until they streamline  it, i recommend slower machines use xbuntu (xfce yay)

---

