---
title: "Curious .... Upgrading Ubuntu!"
date: 2010-04-29
forum: General Help
---

### Post by danioj on 2010-04-29
I am curious.

I see there are many people asking when the official new release will be made available via torrent / download etc. on the forum. Even people who already have the Beta / RC installed (such as myself).

For those people who already have the Beta or RC installed, surely just doing an apt-get upgrade will do the trick without the need to download the full cd image and installing clean again??? 

Have I missed something key here?

---

### Post by 3rdalbum on 2010-04-29
A clean reinstall is not necessary. Just run Update Manager and you'll have the final release version. The difference is only a couple of megabytes and you won't have to download the whole distro again.

---

### Post by danioj on 2010-04-29
OK ... seems I was wrong. But still I don't see why people would be waiting for the torrent or full CD image given a current install.

Sudo apt-get upgrade will upgrade packages only.
[FONT=Verdana]But it seems to upgrade distro you can still use apt:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
[/FONT] [FONT=Verdana]my source: [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)[/FONT]

---

### Post by danioj on 2010-04-29
> **3rdalbum said:**
> A clean reinstall is not necessary. Just run Update Manager and you'll have the final release version. The difference is only a couple of megabytes and you won't have to download the whole distro again.

Ah ... thanks for clarifying 3rdalbum. We just cross posted. :)

---

### Post by Grenage on 2010-04-29
Most of the time, an upgrade is fine, but sometimes you'll have glitches.

Many people simply like a clean install.

---

### Post by mick222 on 2010-04-29
Your rc install is lucid so no need for a dist upgrade . You will probably find few or no updates at the launch .The rc didn't install without using nomodeset so I will probably download the full release when it comes out expect it sometime this afternoon.

---

### Post by 3rdalbum on 2010-04-29
> **Grenage said:**
> Most of the time, an upgrade is fine, but sometimes you'll have glitches.

Many people simply like a clean install.

We're talking about upgrading from the Release Candidate to the final version. The difference is probably only 17 packages totalling 8 mebibytes or something. If you've been following Lucid's development you're probably not averse to the extremely minimal possibility of breakage that could happen when going from RC to final.

---

### Post by Grenage on 2010-04-29
> **3rdalbum said:**
> We're talking about upgrading from the Release Candidate to the final version. The difference is probably only 17 packages totalling 8 mebibytes or something. If you've been following Lucid's development you're probably not averse to the extremely minimal possibility of breakage that could happen when going from RC to final.

Oh fudge, for some reason I was talking about 9.10 to 10.04.  I think I need more sleep, and a lot more coffee.

---

### Post by balaknair on 2010-04-29
> **danioj said:**
> I am curious.

I see there are many people asking when the official new release will be made available via torrent / download etc. on the forum. Even people who already have the Beta / RC installed (such as myself).

For those people who already have the Beta or RC installed, surely just doing an apt-get upgrade will do the trick without the need to download the full cd image and installing clean again??? 

Have I missed something key here?

I've been running 10.04 since Alpha 3 as my main OS on one machine(an old laptop) and on a spare third hard drive(triple booting with XP and Karmic) on another(desktop). And when the final release is out I'll be wiping the laptop and doing a clean install since I've also been testing some other packages(via testing PPAs for XORG, AWN, GNOME Shell etc) and it's pretty messed up. The desktop will see the third drive taken out(till Maverick Alpha 3) and Karmic will be wiped to make way for Lucid.
I also want the CDs so that I can give them to friends and to have a Live Rescue CD when called upon to help with Windows trouble.

So yeah, I'm waiting for Lucid final release to hit the servers.

---

### Post by dino99 on 2010-04-29
> **balaknair said:**
> I've been running 10.04 since Alpha 3 as my main OS on one machine(an old laptop) and on a spare third hard drive(triple booting with XP and Karmic) on another(desktop). And when the final release is out I'll be wiping the laptop and doing a clean install since I've also been testing some other packages(via testing PPAs for XORG, AWN, GNOME Shell etc) and it's pretty messed up. The desktop will see the third drive taken out(till Maverick Alpha 3) and Karmic will be wiped to make way for Lucid.
I also want the CDs so that I can give them to friends and to have a Live Rescue CD when called upon to help with Windows trouble.

So yeah, I'm waiting for Lucid final release to hit the servers.

to remove the "mess" install and run gconf-cleaner and bleachbit, you will see the difference  :P

---

