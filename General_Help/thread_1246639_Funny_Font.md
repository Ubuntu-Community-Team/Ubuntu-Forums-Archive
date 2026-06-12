---
title: "Funny Font"
date: 2009-08-21
forum: General Help
---

### Post by sideaway on 2009-08-21
Hey guys, just wondering, can anyone tell me how to change the default font?

Every time I use Amarok, Gedit, Leafpad or the terminal, I get huge ugly fonts... Can someone tell me how to change it? I'm new at this font editing buiness.... 

Cheers guys :)

[[IMG]http://www.hdimage.org/images/ccgcm8594ss6trdk2x_thumb.jpeg[/IMG]](http://www.hdimage.org/viewer.php?file=ccgcm8594ss6trdk2x.jpeg)

EDIT Before you say it looks fine, please compare with Firefox fonts in the background, I'd like them about that size...

---

### Post by rednano12 on 2009-08-21
The issue is, amaroK is a KDE app, whereas Firefox is designed to fit in whatever DE.

Can you post a screenshot of Gedit/FF or Terminal/FF?

---

### Post by sideaway on 2009-08-21
It's the same font at the same size, I think it's related, i.e, using the same setting?

[[IMG]http://www.hdimage.org/images/n5k5vy5scyo89h4tc2w_thumb.jpeg[/IMG]](http://www.hdimage.org/viewer.php?file=n5k5vy5scyo89h4tc2w.jpeg)

---

### Post by chessnerd on 2009-08-22
System > Preferences > Appearance - You should be able to change system fonts from there.

Hope that was what you were looking for.

---

### Post by sideaway on 2009-08-22
Hey there, I'd prefer not to initialise gnome-appearance-settings or whatever other things it initialises... The only reason it's installed is so I can use Nautilus.

I shouldn't need it to set terminal fonts? Could it be to do with Openbox? I'm not running a Desktop Environment atm...

---

### Post by chessnerd on 2009-08-22
> **sideaway said:**
> Could it be to do with Openbox? I'm not running a Desktop Environment atm...

That might have something to do with it. I'm sure there is a way to set the system fonts in Openbox, but you'd probably have to find some file and modify it to change the fonts. Honestly I've only used Openbox a couple of times so I wouldn't really know... :(

---

### Post by sideaway on 2009-08-22
Ok well you agve me an idea, but lxappearance and gtk-chtheme appear to have no affect on the terminal nor amarok. Oh and nor Leafpad.

Anyone got an idea. I'm currently running Openbox with Gnome uninstalled, and Nautilus installed.

---

### Post by sideaway on 2009-08-22
Well I found the openbox rc...

```
  <theme>
    <name>Fawn</name>
    <titleLayout>DSLIMC</titleLayout>
    <!--
      avaible characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
  -->
    <keepBorder>yes</keepBorder>
    <animateIconify>yes</animateIconify>
    <font place="ActiveWindow">
      <name>Sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="InactiveWindow">
      <name>Sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuHeader">
      <name>Sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuItem">
      <name>Sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="OnScreenDisplay">
      <name>Sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>Normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>Normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
  </theme>
```

That's the theme part, everything is sans 8... which definitely not the size that's in Amarok and the terminal. BTW my emulator is xterm.

---

### Post by sideaway on 2009-08-22
Ok well I edited ~/.kde/share/config/kdeglobals and added
```
[General]
fixed=Monospace,5,-1,5,50,0,0,0,0,0
font=UnDotum,10,-1,5,50,0,0,0,0,0
menuFont=UnDotum,10,-1,5,50,0,0,0,0,0
taskbarFont=UnDotum,10,-1,5,50,0,0,0,0,0
toolBarFont=UnDotum,10,-1,5,50,0,0,0,0,0
```

Where UnDotum,10 = font [size]

Then restarted any kde apps I was using and voila! fonts had changed, for the terminal etc, I had to right click and edit preferences (dumb huh?) :P

---

### Post by chessnerd on 2009-08-22
Glad you got it fixed.

> **sideaway said:**
> for the terminal etc, I had to right click and edit preferences (dumb huh?) :P

Yes, sometimes the simplest solutions are the ones that work. :)

---

### Post by sideaway on 2009-08-22
Hmm that' all fine and dandy, but I went and installed xchat... This came up with massive fonts as well... Is there some fundamental font setting I have wrong (too big) that I can change so I don't have to manually edit the settings? (have to manually edit them for root as well....)

---

