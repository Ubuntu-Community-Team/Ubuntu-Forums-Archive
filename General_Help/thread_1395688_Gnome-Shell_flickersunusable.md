---
title: "Gnome-Shell flickers/unusable"
date: 2010-02-01
forum: General Help
---

### Post by JCoster on 2010-02-01
Alright,
I used to have Gnome Shell working fine but haven't tried it in a couple of months.  
I attempted to start it today
```
gnome-shell --replace
```
..and it loads but it's unusable as it flickers.
The console I load it from goes italic (not really italic but more corrupt) and then whenever i do anything the screen flickers black.
Just wondering whether anyone else has had this experience?  I've done a bit of googling but to no avail..
Before you say it I know GS is still in testing and that it's not stable- just want to give it another go to see progress.
FYI I've installed it from the repos- not built from source.
Cheers

---

### Post by JCoster on 2010-02-04
Sorry- BUMP

---

### Post by ssmithy on 2010-02-05
I can't help you with the Ubuntu repos version, but I'd suggest using a different method to try out GS.  That version is pretty old; you won't see any of the new enhancements/features.  The first post of this thread shows you the different ways to try it out (like building from source or using a PPA).

[http://ubuntuforums.org/showthread.php?t=1305154&highlight=gnome-shell](http://ubuntuforums.org/showthread.php?t=1305154&highlight=gnome-shell)

---

### Post by JCoster on 2010-02-05
Thanks for your reply.  I updated it using the Ricotz test PPA yet I still experience the flickering with black screen whenever an animation occurs?

Cheers,
JC

---

### Post by JCoster on 2010-02-07
FYI:
```

jcoster@jcoster-laptop:~$ gnome-shell --replace
/usr/share/themes/exotic/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/exotic/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/exotic/gtk-2.0/gtkrc:156: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
      JS LOG: GNOME Shell started at Sun Feb 07 2010 20:51:30 GMT+0000 (BST)
      JS LOG: Failed to acquire org.freedesktop.Notifications; trying again

(mutter:9146): GdmUser-WARNING **: Unable to parse history: (null)   1

^CShell killed with signal 2
Checking for Xgl: jcoster@jcoster-laptop:~$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
/usr/share/themes/exotic/gtk-2.0/gtkrc:89: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/exotic/gtk-2.0/gtkrc:90: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/exotic/gtk-2.0/gtkrc:156: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1** (gnome-panel:9161): DEBUG: Adding applet 0.
** (gnome-panel:9161): DEBUG: Initialized Panel Applet Signaler.
glxinfo: symbol lookup error: glxinfo: undefined symbol: glGetConvolutionParameteriv
Comparing resolution (1920x1080) to maximum 3D texture size (): [: 421: -gt: argument expected
[: 421: -gt: argument expected
Passed.
Checking for Software Rasterizer: ** (gnome-panel:9161): DEBUG: Adding applet 1.
** (gnome-panel:9161): DEBUG: Adding applet 2.
** (gnome-panel:9161): DEBUG: Adding applet 3.
** (gnome-panel:9161): DEBUG: Adding applet 4.
** (gnome-panel:9161): DEBUG: Adding applet 5.
Not present. 
Checking for nVidia: ** (gnome-panel:9161): DEBUG: Adding applet 6.
** (gnome-panel:9161): DEBUG: Adding applet 7.
** (gnome-panel:9161): DEBUG: Adding applet 8.
** (gnome-panel:9161): DEBUG: Adding applet 9.
not present. 
Checking for FBConfig: ** (gnome-panel:9161): DEBUG: Adding applet 10.
** (gnome-panel:9161): DEBUG: Adding applet 11.
** (gnome-panel:9161): DEBUG: Adding applet 12.
present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
** (gnome-panel:9161): DEBUG: Adding applet 13.
** (gnome-panel:9161): DEBUG: Adding applet 14.
** (gnome-panel:9161): DEBUG: Adding applet 15.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

```

jcoster@jcoster-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3650
OpenGL version string: 3.2.9232

```

---

### Post by punkrockguy318 on 2010-03-28
I'm also experiencing this.

It has something to do with the fglrx driver.  I have no issues with the ati driver.  Maybe something xorg.conf related?

---

### Post by lesnoland on 2010-06-06
bump

same problem, ati mobility radeon 4550, fglrx

flickers a LOT.

same italic problem.


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.9836 Compatibility Profile Context

Also, I have filed a new bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/591019](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/591019)

Update: I got it to work using this, installing the edgers ppa:

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by Duncan J Murray on 2010-08-24
Hmmm, also suffering a similar problem.  Using ATI radeon 7500 32mb on a T40 thinkpad.

The problem here is that I can't see any of the gnome shell!  It's all black-on-black!

Shame because I wanted to test it and provide feedback...

Duncan.

---

