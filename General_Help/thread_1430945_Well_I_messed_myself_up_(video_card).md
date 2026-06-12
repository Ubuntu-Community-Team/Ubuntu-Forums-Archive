---
title: "Well I messed myself up (video card)"
date: 2010-03-16
forum: General Help
---

### Post by Waveridr85 on 2010-03-16
I installed a new video card (ATI radeon chipset) an was messing with drivers but was not able to get desired results.  They were actually worse than the onboard video on the motherboard (intel GMA x4800).  I installed and un-installed xorg, ati catalyst, proprietary drivers (fglrx), envy which I used to install ati driver and then un-install it.  Nothing worked right.

Decided to go back to the onboard graphics and now they dont work.:confused: 

I am pretty sure its driver related since when I boot I get the "gateway logo" then the white ubuntu logo, but after that it goes blank.  I press cntrl-alt-f1 and a "graphics mode can not be displayed" error from my monitor appears. If I plug the old card in, it works however.

I just want to go to my old settings :icon_frown:

---

### Post by soltanis on 2010-03-16
Did you create an xorg.conf file? I would definitely get confirmation on this, but newer distros by default generate this file automatically (by newer I mean Fedora went this way 2 releases back). If you delete the xorg.conf file that might get the X server to reconfigure itself.

Other methods I know of are running

```

sudo dpkg-reconfigure xserver-xorg

```

Or you might try, if that fails,

```

sudo Xorg -configure

```

When that process is done the X server will tell you where it saved the configuration it created. Move that to /etc/X11/xorg.conf.

These methods all create the mythical Xorg configuration file which, in my previous experience with graphics cards with breaky-prone drivers, is the usual suspect.

My experiences are a year old so, grain of salt.

---

### Post by Waveridr85 on 2010-03-16
> **soltanis said:**
> Did you create an xorg.conf file? I would definitely get confirmation on this, but newer distros by default generate this file automatically (by newer I mean Fedora went this way 2 releases back). If you delete the xorg.conf file that might get the X server to reconfigure itself.

Other methods I know of are running

```

sudo dpkg-reconfigure xserver-xorg

```Or you might try, if that fails,

```

sudo Xorg -configure

```When that process is done the X server will tell you where it saved the configuration it created. Move that to /etc/X11/xorg.conf.

These methods all create the mythical Xorg configuration file which, in my previous experience with graphics cards with breaky-prone drivers, is the usual suspect.

My experiences are a year old so, grain of salt.

I'm sorry for my lack of better terminology, I am very new to ubuntu.  I don't know if I created and xorg.conf file,  I am however showing some when i do a search.  It pulls up:

xorg.conf
xorg.conf.new
xorg.conf-backup_1003...
xorg.conf-backup_2010....
xorg.conf.failsafe
xorg.conf.new

If I try to delete these, it says I do not have permission to do so.

---

### Post by polki@mac.com on 2010-03-16
Just cd to the correct directory:

cd /etc/X11

Then change the name of your xorg.conf:

sudo mv xorg.conf xorg.conf.backup

Type your password when prompted (it won't show you anything as you type it, just type it and hit enter).

Hope that works for you.

---

### Post by mkp123 on 2010-05-12
[COLOR=black]This is a common driver issue.  A new video card with its driver is installed but it does not give its better result. After uninstalling the pack and install the old pack then it works. This is a major issue that is related to new drivers. This issue prevents the installation of new drivers such as video cards etc. The major operating system companies are going to make their operating system update for supporting all the new versions of drivers.[/COLOR][COLOR=black][FONT=&quot]  [/FONT][/COLOR]

---

