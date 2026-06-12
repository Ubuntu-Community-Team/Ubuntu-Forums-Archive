---
title: "Screen Resolution Limited, Need Help Immediately"
date: 2010-04-05
forum: General Help
---

### Post by TheZorch on 2010-04-05
I may have to give up being an Ubuntu user if I can't get help with this problem.  Please, someone out there, I'm a newbie to Linux and I need step-by-step assistance with an issue which has been plaguing me since 8.04.

Ubuntu 7.10 is the last version of the OS which allowed you to "manually" select what the settings for your monitor are in the screen resolution window.  Ubuntu 8.04 to the current version 9.10 doesn't have this anymore.  X.org doesn't properly detect what kind of monitor I have, selects a default, and that's where my problems begin.

After installing Ubuntu I can only select a max resolution of 800x600 "before" installing the drivers for my Nvidia Geforce FX 5600 card.  After the drivers are installed the max resolution I can get is 640x480 which for me is completely UNUSABLE.  Everything is way too big, parts of windows are obscured off screen, and not every window scales properly or lets you scroll down.

I use the Desktop Zoom feature of Compiz Fusion due to my visual disability all the time.  I usually set my desktop to 1024x768 which is the maximum I can raise it to and still be able to mostly see the desktop.  To get around this problem I've been manually editing my xorg.conf file.

I've copied the monitor settings from the xorg.conf of Ubuntu 7.10 and have been pasting them into the xorg.conf files of all of the latest versions I've been using.  This has some unfortunately side-effects.  I currently use 9.10.

1.  The Nvidia X Server Configuration tool cannot save settings to xorg.conf.
2.  I can no longer update the Nvidia drivers when new ones are available via the Hardware Drivers window.

Being a newbie to Linux, I dabbled in 1999 with Redhat, and didn't use Linux again until Wubi became available.  I now install Ubuntu natively and got rid of XP on this machine.  To fix this resolution problem I've searched Google, posted in mailing lists and forums, and even filed a bug report.  I've gotten no assistance.  I can't get any of the things I find searching Google to work, and now I'm getting to the point where I may have to give up being an Ubuntu user if this problem can't finally be resolved.  I've begged and pleaded for the ability to manually change the monitor settings in the screen resolution window be put back in, but it seems that nobody cares.

I need serious step-by-step help.  Whom among you in this community will come forward and help me find a resolution to this problem once and for all.  Not smart-mouthed comments or anti-newbie hate speech which is what I usually get from the Linux community.  

If I cannot get help with this then I'll have to seriously reconsider upgrading to 10.04, which likely won't fix this problem either.  Its sad and a terrible shame that Canonical has let this problem persist for this long.

My system specs:
-- AMD Athlon XP 2000+ 1.2GHz CPU
-- PC Chip K7 mobo (custom built PC)
-- 1GB PC2700 RAM
-- 8x AGP Nvidia Geforce FX 5600 w/256BM DDR RAM
-- 27inch Sun Microsystems Workstation Display (has dual inputs, Sun Workstation and standard PC SVGA, works in Windows XP up to a resolution of 1280x1024)
-- Sound Blaster Live 24-bit sound card
-- Realtek 10/100 Ethernet Adapter
-- NEC DVD-RW Drive
-- 160GB ATA-100 main drive and 80GB ATA-100 secondary

---

### Post by 3rdalbum on 2010-04-05
Have you reported this as a bug? The correct resolution should always be detected.

The Nvidia Settings program can't save to xorg.conf unless you run it as root:

```
sudo nvidia-settings
```

You can create an xorg.conf file by quitting out of X and running the "sudo X -configure" command. So, first log out, and then hit Control-Alt-F2 to get to a terminal. Log into this terminal and type:

```
sudo service gdm stop
sudo X -configure
```

X will put its new configuration file into your home directory - you'll have to move it to replace the existing Xorg.conf. The new Xorg.conf will contain absolutely every piece of information about your graphics card and monitor, including modes (resolutions), so you can edit it and add the correct resolution for your monitor.

When you've done that, you can start up X again:

```
sudo service gdm start
```

I hope this helps. And don't forget: Submit a bug report, the developers have probably never seen this problem because they probably don't have old Nvidia cards.

---

### Post by akvilio on 2010-04-05
I, practically, have the same problem.

I installed ubuntu 7.04 yesterday and since then i can't configure my resolution.
I have a 22" monitor and Geforce 6100 and currently the resolution is 800x640 so that sucks. :cry:
I tried with **[COLOR=Black]Screen Resolution tool, [/COLOR]**[COLOR=Black]i downloaded **NVIDIA-Linux-x86-1.0-8174-pkg1.run **and i have no idea how to install it because i'm a newbie, i tried to install with **restricted drivers manager **but it doesn't work and it returns to the same screen after clicking "Enable Driver".
Even tried downloading the **nvidia-glx** driver but no help from that.


[/COLOR]

---

### Post by TheZorch on 2010-04-05
> **3rdalbum said:**
> Have you reported this as a bug? The correct resolution should always be detected.

The Nvidia Settings program can't save to xorg.conf unless you run it as root:

```
sudo nvidia-settings
```

You can create an xorg.conf file by quitting out of X and running the "sudo X -configure" command. So, first log out, and then hit Control-Alt-F2 to get to a terminal. Log into this terminal and type:

```
sudo service gdm stop
sudo X -configure
```

X will put its new configuration file into your home directory - you'll have to move it to replace the existing Xorg.conf. The new Xorg.conf will contain absolutely every piece of information about your graphics card and monitor, including modes (resolutions), so you can edit it and add the correct resolution for your monitor.

When you've done that, you can start up X again:

```
sudo service gdm start
```

I hope this helps. And don't forget: Submit a bug report, the developers have probably never seen this problem because they probably don't have old Nvidia cards.

I've saved this to a file.  I'm using the Edited XORG.CONF file trick right now for 9.10.  I use this for 10.04 once its finally released.  Hopefully this will work.

I have issued bug reports about this problem and nothing much was done about it.  This problem has gone on long enough.

Therefore, I found the email address for and sent a message directly to "Mark Shuttleworth" detailing the serious consequence for not having the ability to change your monitor settings in the screen resolution window.

---

### Post by one-of-four on 2010-04-05
Also being a "newbie" I understand what you're going through.

I successfully installed the nvidia drivers (and settings utility) using this guide [http://onlyubuntu.blogspot.com/2008/08/howto-install-manually-nvidia-drivers.html]("http://onlyubuntu.blogspot.com/2008/08/howto-install-manually-nvidia-drivers.html") it goes through everything step by step. Make sure to print it out before starting the install process!

If you have mythbuntu the nvidia drivers are already there and you just have to enable them with the restricted drivers utility.

I hope this helps, let me know if it doesn't!

---

### Post by TheZorch on 2010-04-06
> **one-of-four said:**
> Also being a "newbie" I understand what you're going through.

I successfully installed the nvidia drivers (and settings utility) using this guide [http://onlyubuntu.blogspot.com/2008/08/howto-install-manually-nvidia-drivers.html]("http://onlyubuntu.blogspot.com/2008/08/howto-install-manually-nvidia-drivers.html") it goes through everything step by step. Make sure to print it out before starting the install process!

If you have mythbuntu the nvidia drivers are already there and you just have to enable them with the restricted drivers utility.

I hope this helps, let me know if it doesn't!

Thank you.  As I said in my last post I'll try this for 10.04.  If I can get working I'll be happy.  If not, well I've been considering Mandriva.

---

