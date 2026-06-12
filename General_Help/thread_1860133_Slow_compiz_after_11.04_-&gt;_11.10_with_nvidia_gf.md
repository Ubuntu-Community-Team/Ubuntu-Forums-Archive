---
title: "Slow compiz after 11.04 -&gt; 11.10 with nvidia gfx?"
date: 2011-10-14
forum: General Help
---

### Post by falkowich on 2011-10-14
I updated my desktop at work and now I have a  horrible fps. 
Everything worked like a breeze in 11.04 but after the update to 11.10 things  goes really slow. 

Disabled lots of compiz features, but no cigar. 
Updated to bleeding edge drivare via ppa but nope.  
I have the Quadro NVS 290 with two HP monitors.  It looks now that I have to go back to 11.04, and I really like 11.10 on  my other computers. 
Even my laptop and my wifes really old laptop is faster than this..

I tried Unity 2d, gnome-shell but they seemed really slow too.
Done unity --reset, cleaned up unity in dconf, and well anything I can come up with

Any ideas?

--
Regards Falkowich

---

### Post by effenberg0x0 on 2011-10-14
On CompizConfig-Setings-Manager, on the OpenGL plugin, you should disable "Sync to VBlank". 

See if that gives you a better performance. Some Nvidia cards are directly affected by this setting.

Regards,
Effenberg

---

### Post by falkowich on 2011-10-14
> **effenberg0x0 said:**
> On CompizConfig-Setings-Manager, on the OpenGL plugin, you should disable "Sync to VBlank". 

See if that gives you a better performance. Some Nvidia cards are directly affected by this setting.

Regards,
Effenberg

Hi,

I tried some different tweaks in ccsm. Sync to VBlank and "detect refreshrate" in composite.
The thing is that all the different shells feels laggy. But I can only compare to Unity3D beq I haven't used 2D and gnome shell before.

--
Regards falkowich

---

### Post by effenberg0x0 on 2011-10-14
Check your settings at nvidia-settings too. If the card is set to Hight Quality, it gets slower than when its set to Full Performance. You gotta move the slider inbetween these two extremes in a way that it works good to you. You also have VSync in GL there, which affects performance. Same for anti-aliasing and texture sharpening (demand a little more from the card).

Sometimes we get stuck with a /etc/X11/xorg.conf that also does not help. You may try simply mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old and restarting your session, to see if you get any difference in performance. Reverting is just as easy with sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf.

Regards,
Effenberg

---

### Post by falkowich on 2011-10-17
> **effenberg0x0 said:**
> Check your settings at nvidia-settings too. If the card is set to Hight Quality, it gets slower than when its set to Full Performance. You gotta move the slider inbetween these two extremes in a way that it works good to you. You also have VSync in GL there, which affects performance. Same for anti-aliasing and texture sharpening (demand a little more from the card).

Sometimes we get stuck with a /etc/X11/xorg.conf that also does not help. You may try simply mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old and restarting your session, to see if you get any difference in performance. Reverting is just as easy with sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf.

Hi again.

I have now tested out nvidia-settings to. Removed the xorg.conf and restarted.
It seems like it is twinview that is the problem for me.
When I user one monitory everything is handy dandy. But when I start twinview it starting to lag bigtime.

Perhaps a bug req is in order here.
I will check out if there are any previous bugs reported in 11.10 on this.

--
Regards Falk

---

### Post by nPoc on 2011-10-27
I found your issue, and I think I have the identical problem.  No issues until I enabled twinview.  Do you have a resolution, or can you point me to your bug on launchpad?

---

### Post by falkowich on 2011-10-28
> **nPoc said:**
> I found your issue, and I think I have the identical problem.  No issues until I enabled twinview.  Do you have a resolution, or can you point me to your bug on launchpad?
Hi,

I forgot about this post.. Sry..

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/877438](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/877438)

--
Regards Falk

---

### Post by nPoc on 2011-10-28
Well I ran a test last night to check if I could reproduce the problem with only a single display.  Turns out I could reproduce it there as well, it just took a little longer, and wasn't as pronounced.

---

