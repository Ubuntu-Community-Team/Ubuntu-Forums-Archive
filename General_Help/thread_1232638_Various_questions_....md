---
title: "Various questions ..."
date: 2009-08-05
forum: General Help
---

### Post by spikemcc on 2009-08-05
[FONT=Arial][SIZE=3]8.04 (LTS but no lxde) or 8.10 (pigin is better intregrated and lxde is in the official repositories) ?
P.S. 9.04 don't do for me until mesa 7.6 (I hope for it fast) ...

32 bits (more support to add repositories, more supported, more easy, easiest for non 64 bits packages, softwares and games, better support for linux proprietary softwares and games...) or 64 bits (more compiling, more performance but as wine still 32 bits does it still better ?) ?

xfce4 (middleweight, hard for ntfs, no media keyboard shortcuts, better weather applet, well supported ...) , lxde (pure power and speed, hardest, no media keyboard shortcuts, no weather applet, menu has some bugs, ...) or gnome-openbox (original ubuntu perfectly supported but with more speed, more easy to follow tutorials, highly configurable and easiest) ?[/SIZE][/FONT][SIZE=3]

tell me some lightweight apps or good well known apps to try also ... (lxde apps seem good, some cli apps also, wicd ...)

is there a way to know all packages installed by ubuntu-desktop to choose only what I need ?
[/SIZE]

---

### Post by Revolutionary101 on 2009-08-05
I suggest 8.04, 64 bits, and gnome

---

### Post by t0p on 2009-08-05
I prefer 8.10 to 8.04.  For a few reasons, but the main one I can think of right now is that network-manager in 8.10 is better than in 8.04 - it handles wireless networks better for one thing.

I haven't had much experience with wicd.  But it is the network manager that comes with BackTrack4, and I just recently started playing with BT4 pre-final.  So I've messed with wicd a bit there, and I haven't enjoyed it much.  Maybe that's because I'm used to network-manager, but I don't really like the way wicd works.  Of course, maybe with more experience of it I would get to like wicd. Then again, maybe not.

I'm on my 8.04 Xubuntu box right now, and I looked in Synaptic to see what it says about wicd.  And it wasn't there!  I've got all the usual repos enabled, so I don't know why wicd doesn't show up in my Synaptic.  Isn't there a version for 8.04?

Is there a particular reason why you don't want all the software that comes with ubuntu-desktop?  Like a small hard drive or something?  My 8.04 Xubuntu machine started life as default Ubuntu, but it's got only 256MB of RAM so I installed xubuntu-desktop and now use xfce as default.  But I've still got most of the apps that came with the ubuntu-desktop, as well as the xubuntu-desktop ones, and I like it that way because it gives me a nice wide selection of software to choose from.  So, unless you have a pressing reason to keep your number of apps small, I'd suggest you install ubuntu-desktop.  You can still use a lightweight desktop environment, but you'll have the full repertoire of software in case you need it some time.

---

### Post by slakkie on 2009-08-05
> **spikemcc said:**
> 8.04 (LTS but no lxde) or 8.10 (pigin is better intregrated and lxde is in the official repositories) ?
P.S. 9.04 don't do for me until mesa 7.6 (I hope for it fast) ...


I would go for 8.04 or 9.04. If you want for mesa 7.6, 9.10 provides 7.5 afaik (see [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mesa](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mesa) ). So you would need to wait at least for 10.x, where 10.04 is most probably LTS.

From 8.04 you can upgrade to 10.04 directly.

8.04 has lxde:
```

aptitude search lxde
p   lxde                                                                             - Meta-package for the Lightweight X11 Desktop Environment
p   lxde-common                                                                      - the Lightweight X11 Desktop Environment configuration data
p   lxde-settings-daemon                                                             - LXDE settings daemon

```

> 
is there a way to know all packages installed by ubuntu-desktop to choose only what I need ?


```

aptitude -D show ubuntu-desktop
# or
apt-cache -i depends ubuntu-desktop

```

32 bit or 64 bit, I only run 32 bit and have never tried 64 bit ubuntu so can't tell you anything about it.

---

### Post by spikemcc on 2009-08-05
> **t0p said:**
> I prefer 8.10 to 8.04.  For a few reasons, but the main one I can think of right now is that network-manager in 8.10 is better than in 8.04 - it handles wireless networks better for one thing.

I haven't had much experience with wicd.  But it is the network manager that comes with BackTrack4, and I just recently started playing with BT4 pre-final.  So I've messed with wicd a bit there, and I haven't enjoyed it much.  Maybe that's because I'm used to network-manager, but I don't really like the way wicd works.  Of course, maybe with more experience of it I would get to like wicd. Then again, maybe not.

I'm on my 8.04 Xubuntu box right now, and I looked in Synaptic to see what it says about wicd.  And it wasn't there!  I've got all the usual repos enabled, so I don't know why wicd doesn't show up in my Synaptic.  Isn't there a version for 8.04?

Is there a particular reason why you don't want all the software that comes with ubuntu-desktop?  Like a small hard drive or something?  My 8.04 Xubuntu machine started life as default Ubuntu, but it's got only 256MB of RAM so I installed xubuntu-desktop and now use xfce as default.  But I've still got most of the apps that came with the ubuntu-desktop, as well as the xubuntu-desktop ones, and I like it that way because it gives me a nice wide selection of software to choose from.  So, unless you have a pressing reason to keep your number of apps small, I'd suggest you install ubuntu-desktop.  You can still use a lightweight desktop environment, but you'll have the full repertoire of software in case you need it some time.

wicd has a ppa and is on 8.10+ repositories as I remember ...

the interest of a minimal install is to have what you want nothing more, nothing less ...
P.S. Just try to remove evolution to switch to thunderbird, that's why I switch to minimal ...

---

### Post by spikemcc on 2009-08-05
> **slakkie said:**
> I would go for 8.04 or 9.04. If you want for mesa 7.6, 9.10 provides 7.5 afaik (see [http://packages.ubuntu.com/search]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mesa")[?suite=default&section=all&arch=any&searchon=names&keywords=mesa]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mesa") ). So you would need to wait at least for 10.x, where 10.04 is most probably LTS.

From 8.04 you can upgrade to 10.04 directly.

8.04 has lxde:
```

aptitude search lxde
p   lxde                                                                             - Meta-package for the Lightweight X11 Desktop Environment
p   lxde-common                                                                      - the Lightweight X11 Desktop Environment configuration data
p   lxde-settings-daemon                                                             - LXDE settings daemon

```

```

aptitude -D show ubuntu-desktop
# or
apt-cache -i depends ubuntu-desktop

```32 bit or 64 bit, I only run 32 bit and have never tried 64 bit ubuntu so can't tell you anything about it.

lxde is included in 8.10+ repositories only without needing a ppa ...

if mesa 7.6 don't come out soon we won't have it in 9.10, another crap release for old ati cards users in october ... damn !!!

but thanks for the terminal code for ubuntu-desktop dependances !!!

---

### Post by slakkie on 2009-08-06
You could ask the guys in #ubuntu+1 or in the karmic development forums wheter mesa will be 7.5 or that they will include 7.6 (or up)..

---

