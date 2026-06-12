---
title: "Ubuntu 10.04 64x + flash player + compiz"
date: 2010-06-22
forum: General Help
---

### Post by gufide on 2010-06-22
I have a real problem, I upgrade to ubuntu 10.04 and now I can't click on flash applications. The only solution I found is to disable compiz. I search on the forum and I doesn't found something useful. Please, help me...
Thank you

---

### Post by hotnikkelz on 2010-06-22
64 bit Flash drivers for LInux has been discontinued by Adobe. Apparently you can install the 32 bit drivesr by going into the synaptic manager and install the flash plugin. Should work i think, although never tried it personally 
instructions
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

---

### Post by gufide on 2010-06-22
I install it with ubuntu software center, that's right?

---

### Post by bowens44 on 2010-06-22
> **gufide said:**
> I install it with ubuntu software center, that's right?

You would be better off to do a google search. There are several scripts available that install the 64 bit version on lucid and it works well.

---

### Post by gufide on 2010-06-22
Ho! Thank you, I found it! I found a script here: [http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html) 
It work!:guitar:

---

### Post by lovinglinux on 2010-06-22
> **gufide said:**
> Ho! Thank you, I found it! I found a script here: [http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html](http://helpforlinux.blogspot.com/2010/05/install-flash-player-10-on-ubuntu-1004.html) 
It work!:guitar:

You shouldn't be using the 64bit version, since it has a critical vulnerability.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

To fix the issue with the buttons do this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by jpvelasquez on 2011-01-28
I have an ASUS G60JX laptop with a NVIDIA GeForce GTS 360M (1G). I've been having several problems with it since I owned it. I tried upgrading NVIDIA drivers permanently and I never got a decent laptop performance. Everytime I enable compiz, not only any flash video gets slow and black stripes appear on it, but any other video(movie player, VLC, etc) and the whole laptop gets slow and the laptop heats a lot, not mention the fan goes completely crazy. I tried the flash-aid and it says I already have the best plugins for my architecture.
I bought this laptop thinking that I would have been able to enjoy a very high video performance, but by this time is only a very expensive piece of crap.

Hope you guys can help me.

---

### Post by lovinglinux on 2011-01-29
> **jpvelasquez said:**
> I have an ASUS G60JX laptop with a NVIDIA GeForce GTS 360M (1G). I've been having several problems with it since I owned it. I tried upgrading NVIDIA drivers permanently and I never got a decent laptop performance. Everytime I enable compiz, not only any flash video gets slow and black stripes appear on it, but any other video(movie player, VLC, etc) and the whole laptop gets slow and the laptop heats a lot, not mention the fan goes completely crazy. I tried the flash-aid and it says I already have the best plugins for my architecture.
I bought this laptop thinking that I would have been able to enjoy a very high video performance, but by this time is only a very expensive piece of crap.

Hope you guys can help me.

Please go to Flash-Aid help tab, generate a report and post the results.

---

### Post by The Chef on 2011-05-13
I did all this with Flash-Aid but still had the Flash freezing issue on a 64-bit i5 processor (onboard HD graphics) until in my Shuttle Bios, I set IGD Graphics Mode to 64 MB (the lowest) and DVMT Memory to 128 MB (the lowest).  No ill performance effects that I notice, even editing HD video.  I have had hundreds of hours of processing since with no crash.  I hope this helps.  (Also, I still have Compiz "System/Preferences/Appearance" set on "normal" not "extra".  Not interested in tempting fate.)

---

