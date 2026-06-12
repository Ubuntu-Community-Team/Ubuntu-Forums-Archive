---
title: "Display doesn't power off - g-p-m and DPMS!?"
date: 2006-06-03
forum: General Help
---

### Post by Jingo on 2006-06-03
Using gnome-power-manager (System->Settings->Power manager) I am able to set the timeout when my display should power off.
But it never happens! I tried all settings.

Screensavers starts fine at whatever timing I set, but I would like it to power off instead (or later).

xset -q gives me:
```
$ xset q | grep -A3 ^DPMS
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
```

I can set the DPMS timeout using xset dpms 600 600 600, but as soon as I change the settings using gnome-power-manager its reset to "0 0 0".

Whats wrong? Am I the only one having the issue?
What should I do about it?

---

### Post by 5-HT on 2006-06-03
It seems like the DPMS option in gnome-power-manger adds the delay set for gnome-screensaver in timing the 'inactivity' period.

For me, if I have the gnome-screensaver set to come on in 10 minutes and gnome-power-manger set to come on in 10 minutes, the display will go to sleep after 20 minutes.

Could that be what's happening for you? Or is it something else (xset shows DPMS is completely disabled for me, but the monitor does go to sleep after gnome-screensaver + gnome-power-manger inactivity periods are reached)?

One thing that bugs me about gnome-power-manager, is that you can only put the monitor to sleep. Turning it off completely, or even having it suspend, would be much better from a power-saving perspective.
Unfortunately, any time I go and change the DPMS options via xset or xorg.conf, as you mentioned, gnome-power-manager overrides them.

If you'd like the other DPMS options, completely disabling/uninstalling gnome-power-manager may be necessary.

HTH

---

### Post by frenkel on 2006-06-03
[QUOTE=Jingo]Using gnome-power-manager (System->Settings->Power manager) I am able to set the timeout when my display should power off.
But it never happens! I tried all settings.

Screensavers starts fine at whatever timing I set, but I would like it to power off instead (or later).

xset -q gives me:
```
$ xset q | grep -A3 ^DPMS
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
```

I can set the DPMS timeout using xset dpms 600 600 600, but as soon as I change the settings using gnome-power-manager its reset to "0 0 0".

Whats wrong? Am I the only one having the issue?
What should I do about it?[/QUOTE]

Did you even search the forum? There are quite some few threads about this.
For example this thread: [http://ubuntuforums.org/showthread.php?t=179262](http://ubuntuforums.org/showthread.php?t=179262)
In this post I explain how to solve the problem: [http://ubuntuforums.org/showpost.php?p=1033384&postcount=5](http://ubuntuforums.org/showpost.php?p=1033384&postcount=5)
And here is the upstream explanation: [http://live.gnome.org/GnomePowerManager/Faq#head-1d3b2b44760600722c7c7873d0512150a47ad358](http://live.gnome.org/GnomePowerManager/Faq#head-1d3b2b44760600722c7c7873d0512150a47ad358)

---

### Post by HydroDiOxide on 2006-07-13
Can't get my monitor to standby either. I've tried the power manager and xscreensaver, but it just won't work. Very annoying since I always forget to turn the thing off when I go take a shower, walk the dog go running or whatever.

So, if anyone knows how to fix the standby mode problem... Juicy detail: Ubuntu could not autodetect my screen automatically so I had to edit my xorg.conf (to higher resolutions).

---

### Post by orb9220 on 2006-07-13
Found this one on google

[http://shallowsky.com/linux/x-screen-blanking.html](http://shallowsky.com/linux/x-screen-blanking.html)

My problem is I want the monitors to always stay ON and I turn off by switch.

DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Enabled
  Monitor is On

I have commented out:  Option "DPMS" on both monitors and xset sets them anyway when it said it used the xorg.conf file.

File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

So what jldsl is going On here and where can i edit the xset values?

---

