---
title: "ATI driver problems"
date: 2006-06-02
forum: General Help
---

### Post by nbx909 on 2006-06-02
I have a radeon 9600 pro and when i first installed dapper today i did a glxgears test and i got a range of 900-4000 depending if i was reading email and such the main mean was ~1,000 fps. Then i was like "wow! I bet this will pwn with the driver installed!" So i installed the xorg-driver-fglrx from the repos and i got crappy fps like 100 fps. After i removed the driver and restored the old xorg.conf it's back to 900-4000. So is there some other technique i could try or is that a good range for an ati card?

---

### Post by jecos on 2006-06-02
First of all, **glxgears should not be tested in no way shape or form to measure driver speed. Its there to show that you have acceleration of some sort.**

By default the r300 driver is installed.  Its not complete like fglrx but its close behind and will probably stay behind fglrx in features for a while.. Use whichever works for you.

---

### Post by nbx909 on 2006-06-02
what is a good way to test drivers then?

---

### Post by seth0x2b on 2006-06-02
```
fgl_glxgears
``` if the fglrx driver is active.

Cheers

---

### Post by djsroknrol on 2006-06-02
If I might add here....

I'm using the "Radeon" driver, which is compatable with that card and a lot more stable for you...

I'm not using XGL/compiz but my other eye candy (3Ddesk, Gcompmgr, etc) works pretty good with it..

---

### Post by HankB on 2006-06-02
[QUOTE=seth0x2b]```
fgl_glxgears
``` if the fglrx driver is active.

Cheers[/QUOTE]
```

hbarta@baobab:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

hbarta@baobab:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Floating point exception
hbarta@baobab:~$

```

This is on a laptop with an ATI video card.

If I run glxgears, it sucks up all of my CPU and never seems to write anything to STDOUT. How long before it writes anything?

---

### Post by joshrobinson on 2006-06-02
ususally within the first second it posts an output of how many fps

whats the spec's on your laptop

---

### Post by wanger123 on 2006-06-02
Hi Hank, I think a lot of people have probs with the X200 card and ATI drivers. Here is a guy who got it working on a Toshiba with another distro

[http://www.pclinuxos.com/forum/index.php?topic=3988.0](http://www.pclinuxos.com/forum/index.php?topic=3988.0)

Note: It says /.ati.run towards the bottom of the page

I think it should be ./ati.run

cheers

wanger

---

### Post by joshrobinson on 2006-06-02
[QUOTE=wanger123]Hi Hank, I think a lot of people have probs with the X200 card and ATI drivers. Here is a guy who got it working on a Toshiba with another distro

[http://www.pclinuxos.com/forum/index.php?topic=3988.0](http://www.pclinuxos.com/forum/index.php?topic=3988.0)

Note: It says /.ati.run towards the bottom of the page

I think it should be ./ati.run

cheers

wanger[/QUOTE]

yeah its ./ati.run   but make sure you rename the driver to ati.run.. instead of ati and the version number.run

---

### Post by HankB on 2006-06-02
[QUOTE=wanger123]Hi Hank, I think a lot of people have probs with the X200 card and ATI drivers. Here is a guy who got it working on a Toshiba with another distro

[http://www.pclinuxos.com/forum/index.php?topic=3988.0](http://www.pclinuxos.com/forum/index.php?topic=3988.0)

Note: It says /.ati.run towards the bottom of the page

I think it should be ./ati.run

cheers

wanger[/QUOTE]

Hi, thanks. I wish I knew what he did.

What did he download? From where? What did he rename to ati.run?

What did fglxinfo display that it was supposed to?

I don't have any reason to believe that my stuff isn't working. I can see that the display is runing faster.

I'm mainly curious why the glxgears doesn't report a frame rate.

thanks,
hank

---

### Post by Kilz on 2006-06-02
[QUOTE=HankB]Hi, thanks. I wish I knew what he did.

What did he download? From where? What did he rename to ati.run?

What did fglxinfo display that it was supposed to?

I don't have any reason to believe that my stuff isn't working. I can see that the display is runing faster.

I'm mainly curious why the glxgears doesn't report a frame rate.

thanks,
hank[/QUOTE]

I think the reason it doesn't is because people think its some kind of benchmark and complain when it changes from driver to driver. If you really want to see the readout type 
glxgears -printfps
and it will give you a fps number.

---

### Post by HankB on 2006-06-02
Oh, yeah. System specs.

HP L2000 laptop - M37 AMD Turion (with 64 bit install) 2 MHz processor.
2GB RAM
ATI Radeon XPRESS 200M  (video, courtesy of the ATI chip)
128 MB shared video RAM (IIRC)

I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and the manual step rather than aticonfig --initial 
Then I had to "NoAccel" option for the video device, leaving that section:
```

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver      "fglrx"
###     Option      "NoAccel"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:5:0"
EndSection

```

and dmesg shows:
```
hbarta@baobab:/etc/X11$ dmesg | grep fglrx
[   61.120602] [fglrx] Maximum main memory to use for locked dma buffers: 1764 MBytes.
[   61.120740] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[   64.144097] [fglrx] total      GART = 67108864
[   64.144104] [fglrx] free       GART = 51118080
[   64.144106] [fglrx] max single GART = 51118080
[   64.144109] [fglrx] total      LFB  = 128118784
[   64.144111] [fglrx] free       LFB  = 120254464
[   64.144113] [fglrx] max single LFB  = 120254464
[   64.144115] [fglrx] total      Inv  = 0
[   64.144116] [fglrx] free       Inv  = 0
[   64.144118] [fglrx] max single Inv  = 0
[   64.144120] [fglrx] total      TIM  = 0

```

Haven't tried 
    sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
yet.

---

### Post by HankB on 2006-06-04
Now I recall why I didn't try this before. The fglrx drivers hang my laptop when it resumes from suspend to RAM. I shuld probably try hibernate, but with breezy it wouldn't resume without hanging.

So it looks like I'm back to the dog slow stock drivers because suspend is important to me. :(

Thanks for the help. One of the benefits of running Ubuntu (aside from the ease of installation and upgrade) is having folks here in the forums that are so willing to help.

---

