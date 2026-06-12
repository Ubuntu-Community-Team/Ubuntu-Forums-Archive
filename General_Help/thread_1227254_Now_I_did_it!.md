---
title: "Now I did it!"
date: 2009-07-30
forum: General Help
---

### Post by n2stc on 2009-07-30
I am running Jaunty KDE on a Gateway desktop with a Radeon 7200 video card.  I have been searching in vain for good video driver so I can set the refresh rate higher than 60Hz.  Following another post I deleted all Xorg-video-driver packages.  Now I can't boot past a shell prompt.  2 questions

What is the best HOW to to solve my video driver problem?
Is there a way to get back to the original packages w/o a total re-install?
Would re-instaaling wipe out all my settings & apps?

I know, that's 3.

Thanks,
Stan:confused:

---

### Post by zzzBrett on 2009-07-30
> **n2stc said:**
> I am running Jaunty KDE on a Gateway desktop with a Radeon 7200 video card.  I have been searching in vain for good video driver so I can set the refresh rate higher than 60Hz.  Following another post I deleted all Xorg-video-driver packages.  Now I can't boot past a shell prompt.  2 questions

What is the best HOW to to solve my video driver problem?
Is there a way to get back to the original packages w/o a total re-install?
Would re-instaaling wipe out all my settings & apps?

I know, that's 3.

Thanks,
Stan:confused:


Before considering reinstalling ubuntu and starting everything over, first try to fix your problem.  See if this helps (execute in shell prompt):

```
dpkg-reconfigure xserver-xorg 
```

---

### Post by n2stc on 2009-07-30
Thanks will do, later.

---

### Post by n2stc on 2009-07-30
What is the best HOW to to solve my video driver problem?

Anyone?

---

### Post by afroman10496 on 2009-07-30
> **n2stc said:**
> What is the best HOW to to solve my video driver problem?

Anyone?
This is only a guess, but how about going to the root prompt and inserting the Live CD? I think it will ask if you want to install packages from it, if it does, say yes.

---

### Post by Zorael on 2009-07-30
Removing all video drivers generally does that. ;3

Are you connected to the internet/your local network via a cable with DHCP (automatic IP assignment) enabled? If so, boot up in recovery mode, pick netroot, and then reinstall those video drivers from the repositories.
```
# aptitude install xserver-xorg-video-all
# exit
```
Then pick resume.

If you're connected via wireless or via wired, static IP, there's a few more commands you have to run first.

---

### Post by n2stc on 2009-07-30
> **Zorael said:**
> Removing all video drivers generally does that. ;3

Are you connected to the internet/your local network via a cable with DHCP (automatic IP assignment) enabled? If so, boot up in recovery mode, pick netroot, and then reinstall those video drivers from the repositories.
```
# aptitude install xserver-xorg-video-all
# exit
```
Then pick resume.

If you're connected via wireless or via wired, static IP, there's a few more commands you have to run first.

That's better.  THANKS!  I even have more resolution choices now.  Still only one refresh rate though.  I seem to remember a file where that needs to be added as an option.
The display in lshw is listed as unclaimed too.

---

### Post by Zorael on 2009-07-31
> **n2stc said:**
> That's better.  THANKS!  I even have more resolution choices now.  Still only one refresh rate though.  I seem to remember a file where that needs to be added as an option.
The display in lshw is listed as unclaimed too.
Mhm, /etc/X11/xorg.conf, but that was in the olden days. Now everything is autodetected and autoconfigured by the Hardware Abstraction Layer (HAL), and as such it's even more difficult to tweak when it doesn't get something right.

What is the terminal output of the following?
```
$ xrandr
```
That should list the available resolutions and refresh rate combinations X is told is available for your current videocard + monitor setup. On my teeny netbook screen;
```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 2048 x 2048
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       **60.0*+**
   640x480        **59.9**
```
The second column is, naturally, the refresh rate. LCD screens don't behave the same way as CRT screens do, so 60hz is natural. 59.9 is just 60 hit by a case of unfortunate rounding (for all intents and purposes).

---

### Post by n2stc on 2009-08-15
[SOLVED]  It turns out I had a hardware problem!  Th KBD switch I was using must not have connected all of the lines.  It is a KVM MT-270S.  When I plugged the monitor in directly I get good resolution and scan rates.  
Thanks to those who replied, and those who thought about it.

:) S

---

