---
title: "Why does 11.10 boot so slow?"
date: 2011-11-01
forum: General Help
---

### Post by mips on 2011-11-01
Anyone know the reasons why the boot speed took a knock in this release?

---

### Post by Mezzoforte on 2011-11-01
The 64-bit version seemed a little bit better. I agree though, the regular version is surprisingly slow. A tad disappointed... More disappointing though is the time it takes to switch users.

---

### Post by wolfen69 on 2011-11-01
I guess it would also depend on your hardware. But a few extra seconds to boot up doesn't bother me at all. I never shut down my desktop to begin with, so it's no big deal to me. (I seed ubuntu iso's 24/7)

Ubuntu runs so well for me that it wouldn't matter if it took twice as long as before to boot. It's well worth the wait to me. ;)

---

### Post by cariboo on 2011-11-01
Can you post a bootchart, so we can see? My Oneiric system boots in about 43 seconds according to bootchart, but it seems to need to re-profile ureadahead every time I use it, because of so many updates.

---

### Post by Copper Bezel on 2011-11-02
I could swear I get to LDM on 11.10 faster than I get to GDM on 11.04, with both of them on ext4. I haven't installed bootchart on my 11.10 side, so all I can go on is subjective experience here, but I did not experience any serious regression (quite the opposite, as far as I can tell.)

---

### Post by Roasted on 2011-11-02
Hmm, booting pretty snappy here. Definitely snappier than 11.04 was on all of my machines, which include:

CR48 Atom Netbook
AMD Single Core Netbook
Core 2 Duo Desktop
i3 2100 Desktop
Quad Core Desktop

*shrug*

---

### Post by mips on 2011-11-02
> **cariboo907 said:**
> Can you post a bootchart, so we can see? My Oneiric system boots in about 43 seconds according to bootchart, but it seems to need to re-profile ureadahead every time I use it, because of so many updates.

I just ran Bleachbit as a normal user and it cleaned up about 400MB of stuff. I rebooted and then rebooted again and now things are MUCH faster.

Here is the bootchart from my last boot:
[[img]http://ompldr.org/tYjNiOA[/img]](http://ompldr.org/vYjNiOA)


Here is the bootchart from my first boot today:
[[img]http://ompldr.org/tYjNiYQ[/img]](http://ompldr.org/vYjNiYQ)

System: Q6600 2.4GHz, 4GB RAM, 7200rpm HDD
OS: Ubuntu 11.10 64-bit Base Install (no Unity/Gnome3) with Xubuntu-Desktop

Since the first install bootup was very slow compared my previous distro, Chrunchbang XFCE 64-bit.

Any idea why this happened? At least it is sorted now :)

Edit: I tried e4rat initially but I would not get my plymouth splash or logout splash and saved 7sec back then. Wonder if I will gain anything now and if there is a fix for the splash issue.

---

### Post by philinux on 2011-11-02
Moved to General Help.

---

### Post by Roasted on 2011-11-02
I wonder if that fix will help already fast machines boot faster? What exactly does it do? Just remove unnecessary cache or something?

---

### Post by mips on 2011-11-03
> **Roasted said:**
> I wonder if that fix will help already fast machines boot faster? What exactly does it do? Just remove unnecessary cache or something?

What fix?

---

### Post by Roasted on 2011-11-03
> **mips said:**
> What fix?

> **mips said:**
> I just ran Bleachbit as a normal user and it cleaned up about 400MB of stuff. I rebooted and then rebooted again and now things are MUCH faster.



I never heard of this before. Makes me wonder if it's worthwhile to run as a part of every post-setup?

---

### Post by Hylas de Niall on 2011-11-03
I'm looking at well over 70secs ATM - I'll try Bleachbit and see what happens.
Thanks for the pointers!
:)

---

### Post by Gremlinzzz on 2011-11-03
A watched pot never boils:popcorn:

---

### Post by jfd3220 on 2011-11-27
Are people who did a clean install of 11.10 finding it slow, or is it just the upgraders? I have upgraded, because I have a bunch of applications installed that I don't want to have to reinstall.  If this slowdown is only an issue for people who have upgraded then it may be worth doing a clean install.

---

### Post by vasa1 on 2011-11-28
> **jfd3220 said:**
> Are people who did a clean install of 11.10 finding it slow, or is it just the upgraders? I have upgraded, because I have a bunch of applications installed that I don't want to have to reinstall.  If this slowdown is only an issue for people who have upgraded then it may be worth doing a clean install.

I did an upgrade from 11.04 to 11.10. Start maybe marginally slower about 45 sec. It doesn't worry me.

---

