---
title: "Working: Svideo out with oss and ATI xpress 200m"
date: 2009-11-20
forum: General Help
---

### Post by homerhomer on 2009-11-20
I recently figured out get my svideo working with my old compaq v2000 laptop with ati xpress 200m. 


This really comes in handy when wanting to watch videos off the Internet onto at television. 

I'm using the default open source radeon driver that comes with Karmic

Attached is my xorg.conf file and two other files I run to turn Svideo on and back off. 


Hope this helps someone.

---

### Post by Wittank22 on 2010-01-17
HomerHomer:

Thanks a million for posting this solution!  I have a Compaq Presario V5000 with an AMD Sempron and an ATI Radeon Xpress 200M card.  The script worked like a champ!  It's movie time now!

Bump! Bump!

---

### Post by jmhkk on 2010-02-20
I also have a Compaq Presario V2000 with the ATI Radeon Xpress 200M and I can't find my original Xorg.conf file. Didn't Karmic get rid of the xorg.conf file altogether?

Whenever I try to copy the xorg.conf file in etc/X11, it says "permission denied"
When I run the other 2 files, it just sets my main monitor in a lower resolution.

Can anyone help?

---

### Post by muzikoverdose on 2010-02-25
this has worked wonderfully for me.  however, how would one make it a permanent solution so i dont have to run the svideo on file each time.

---

### Post by DandyAndy on 2010-03-24
So homerhomer any clues on what could possibly be wrong if i get a flickering black n white screen when trying your fix? Flickering as in a lot of black and white stuff, indistinguishable to my weak human eye. It changes with what i do in the laptop screen so at least i can drop the idea of no connection at all.

I've spent a day at this and i think you've brought me closer than ive been so far. The only clue i get when running you're Svideo_on script is this message in the terminal:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25

Googling generates pretty poor results for me.


This is homerhomers script if t helps any one else who wants a go at helping:

```
#!/bin/bash
xrandr -s 800x600
xrandr --newmode 800x600 38.25 800 832 912 1024 600 603 607 624 -hsync +vsync
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600



```

I've also got this error going for me when using another script running a few xrandr commands.
```

xrandr: cannot find mode 800x600
Found Xv 2.2
XV_CRTC set to 1

```

That script would be the following:
```

xrandr --output VGA-0 --mode 800x600
        xrandr --addmode S-video 800x600
        xrandr --output S-video --mode 800x600 --set tv_standard pal
        xvattr -a XV_CRTC -v 1

```

---

### Post by gorghoa on 2010-05-02
Hey there,

Scripts worked fine ith Karmic on a compaq presario V5000, but since I've upgraded to lucid, they don't work anymore.

Do you have the same problem ? I did an upgrade from karmic and not a full installation.

Have a nice day.

Gorghoa

---

### Post by homerhomer on 2010-05-03
Sorry to be MIA with this one. I messed up my power cable for my laptop and just ordered one on ebay. I should be able to give this another shot by the end of the week.

---

### Post by gorghoa on 2010-05-06
Hi, I think I could wait until there ^^ (I've downgraded to karmic for now... )

By the way, i've reported a bug on launchpad : [https://bugs.launchpad.net/bugs/573550](https://bugs.launchpad.net/bugs/573550)

The bug has been confirmed for [xserver-xorg-video-ati  (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati")

have a nice day

---

### Post by jmort253 on 2010-05-30
I struggled with flashing with my svideo connection on an hp ze2000 laptop.  I finally realized that my svideo would only come up if I had a video playing in vlc player.  Without this app, the tv either just flashed or didn't do anything at all.

If you experience flashing when trying to enable svideo, try running the xrandr commands with a video running.  

James

---

### Post by efflandt on 2010-05-30
Or if you go higher class and connect to an HDTV with VGA, it defaults to 1024x768 for both displays. I use xrandr to turn off the laptop display and switch to an appropriate video mode.  Unfortunately, the max resolution of the 200M on my Compaq Presario V2000 is 1360x1360, but xrandr already listed a 1360x768 mode that should work with most 720p or 1080p displays (no xorg.conf needed).

I just created a launcher in the top bar to run as "Application in Terminal":
Name: HDTV
Command: xrandr --output LVDS --off --output VGA-0 --mode 1360x768
Comment: Switch to HDTV
Icon: gsd-xrandr.svg (video screen)

Just in case it is hard to read, there are double dash prefixes on xrandr parameters.  If you log out of X things go back to defaults.

---

### Post by ixifx on 2010-07-14
I have this same laptop, got it for $40 a couple years ago.  last year, the backlight went out, and I have to connect to a standard monitor to use it.  I'm wondering if anybody has been able to get the s-video and the external monitor to work simultaneously, because this isn't working for me...

---

### Post by TaoJoannes on 2011-01-14
What's cool is that this worked.

What's not cool is that it showed everything EXCEPT the video I wanted to watch.

---

### Post by bigredphil on 2011-07-17
> **jmhkk said:**
> I also have a Compaq Presario V2000 with the ATI Radeon Xpress 200M and I can't find my original Xorg.conf file. Didn't Karmic get rid of the xorg.conf file altogether?

Whenever I try to copy the xorg.conf file in etc/X11, it says "permission denied"
When I run the other 2 files, it just sets my main monitor in a lower resolution.

Can anyone help?

I'm having the same problem as jmhkk. Has this been solved?

---

### Post by merval on 2011-09-20
> **bigredphil said:**
> I'm having the same problem as jmhkk. Has this been solved?

Your getting that error because you aren't running the script as root. be sure your using sudo when using the script.

---

### Post by merval on 2011-09-20
If you can't find your xorg.conf file, you can also open a terminal and type

```
updatedb
```

and then

```
locate xorg.conf
```

99.9% of the time it will be located at /etc/X11/xorg.conf

---

