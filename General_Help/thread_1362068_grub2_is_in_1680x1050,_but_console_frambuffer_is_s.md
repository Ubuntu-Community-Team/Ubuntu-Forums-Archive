---
title: "grub2 is in 1680x1050, but console frambuffer is still low-res"
date: 2009-12-22
forum: General Help
---

### Post by aznranndydraman on 2009-12-22
Hi,

I just installed 9.10 and I have been messing with grub 2 for a bit. It use to be that we enable fbcon and add the vga=.... parameter then usplash and console framebuffer resolutions are set.

Now grub2 is using the GRUB_GFXMODE, and is able to have usplash at the right resolution, but after boot the console is still at a really low resolution. I did lsmod and have gotten:```
Module                  Size  Used by
fbcon                  41344  0 

```
Can someone offer some pointers or suggestions?

Thanks in advance.

---

### Post by GrzegorzJ on 2009-12-30
Hi, I used tip from: [http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

means:
in /etc/grub.d/00_header

after:
```
set gfxmode=${GRUB_GFXMODE}
```I added:
```
set gfxpayload=keep
```now it is stored, even after update-grub (which you should run),
and console uses resolution from grub (I have also set 1680x1050).
I use debian squeeze, but I believe that in this situation it will be the same.

---

### Post by Leppie on 2009-12-30
yes, adding the set gfxpayload=keep option should resolve this.

---

### Post by aznranndydraman on 2010-01-06
Thanks a lot guys, I'll try it as soon as I get a chance and confirm whether it worked or not.

---

### Post by miromiro on 2010-01-25
I have been searching for a solution to this issue. My Grub2 menu displays correctly at 1680x1050 but once I switch to TTY1-6 I am back at 1280x1060.

I tried adding ```
set gfxpayload=keep
``` to /etc/grub.d/00.header but that just rendered the console inoperable (a blinking flat cursor top left & no response)...

Surely someone has cracked this? It seems so, what's the word?, oh -- basic.

---

### Post by Leppie on 2010-01-25
> **miromiro said:**
> I have been searching for a solution to this issue. My Grub2 menu displays correctly at 1680x1050 but once I switch to TTY1-6 I am back at 1280x1060.

I tried adding ```
set gfxpayload=keep
``` to /etc/grub.d/00.header but that just rendered the console inoperable (a blinking flat cursor top left & no response)...

Surely someone has cracked this? It seems so, what's the word?, oh -- basic.
you should check your xorg.conf, especially the device and monitor sections.

---

### Post by pbrane on 2010-01-25
I have tried the method described by Leppie several times and it doesn't work for me in Ubuntu. There seems to be an issue with the framebuffer. If I comment out vesafb and fbcon in the blacklist file the console fails. if I don't comment them out the console is just a blinking cursor. I'm using grub2. The only method that works is **vga=xxx**. I know this issues a warning and may not work one day, but the other method simply doesn't work. I have even asked about it on #grub IRC. It apparently does work in some other distros. **gfxmode** does work, the grub splash screen is at the resolution I set it for. I found several forums where the **gfxpayload** method is successfully used but none of those methods work for me.

Let us know if you get it working with **gfxpayload**.

---

### Post by Leppie on 2010-01-25
> **pbrane said:**
> I have tried the method described by Leppie several times and it doesn't work for me in Ubuntu. There seems to be an issue with the framebuffer. If I comment out vesafb and fbcon in the blacklist file the console fails. if I don't comment them out the console is just a blinking cursor. I'm using grub2. The only method that works is **vga=xxx**. I know this issues a warning and may not work one day, but the other method simply doesn't work. I have even asked about it on #grub IRC. It apparently does work in some other distros. **gfxmode** does work, the grub splash screen is at the resolution I set it for. I found several forums where the **gfxpayload** method is successfully used but none of those methods work for me.

Let us know if you get it working with **gfxpayload**.
try the following:
```
set gfxpayload=XXX  ##replace with the desired resolution + color depth. e.g.: 1024x768x32
```

---

### Post by miromiro on 2010-01-27
> **Leppie said:**
> you should check your xorg.conf, especially the device and monitor sections.

There isn't much in there:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by Leppie on 2010-01-27
this is a sample piece of a xorg.conf:
```
Section "Device"
      Identifier       "nVidia Corporation NV17 [GeForce4 MX 440]"
      Driver             "nvidia"
      Busid            "PCI:1:0:0"
      Option             "AddARGBVisuals"      "True"
      Option             "AddARGBGLXVisuals"      "True"
      Option             "NoLogo"            "True"
      Option         "UseEdidDpi"              "FALSE"
         Option         "DPI"                "96 x 96"
EndSection

Section  "Monitor"
      Identifier       "Generic Monitor"
      ModelName          "COMPAQ V710"
      Option            "DPMS"
      HorizSync       30 - 85
      VertRefresh        50.0 - 160.0
      DisplaySize       289 203
EndSection

Section  "Screen"
      Identifier      "Default Screen"
      Device             "nVidia Corporation NV17 [GeForce4 MX 440]"
      Monitor            "Generic Monitor"
      Defaultdepth      24
      SubSection  "Display"
            Depth      1
            Modes             "1600x1200"      "1280x1024"      "1024x768"      "800x600"       "720x400"      "640x480"
      EndSubSection
      SubSection  "Display"
            Depth      4
            Modes             "1600x1200"      "1280x1024"      "1024x768"      "800x600"       "720x400"      "640x480"
      EndSubSection
      SubSection  "Display"
            Depth      8
            Modes             "1600x1200"      "1280x1024"      "1024x768"      "800x600"       "720x400"      "640x480"
      EndSubSection
      SubSection  "Display"
            Depth      15
            Modes             "1600x1200"      "1280x1024"      "1024x768"      "800x600"       "720x400"      "640x480"
      EndSubSection
      SubSection  "Display"
            Depth      16
            Modes             "1600x1200"      "1280x1024"      "1024x768"      "800x600"       "720x400"      "640x480"
      EndSubSection
      SubSection  "Display"
            Depth      24
            Modes             "1600x1200"      "1280x1024"      "1024x768"      "800x600"       "720x400"      "640x480"
      EndSubSection
EndSection
```

did you ever run nvidia-xconfig?

---

### Post by miromiro on 2010-01-27
> **Leppie said:**
> this is a sample piece of a xorg.conf:
..snip..
did you ever run nvidia-xconfig?

Thanks Leppie: not that I recall. 

However, I'm not clear on why I should be looking at xorg.conf when I am trying to sort out console resolution (X doesn't even need to be running)?

---

### Post by Leppie on 2010-01-27
> **miromiro said:**
> Thanks Leppie: not that I recall. 

However, I'm not clear on why I should be looking at xorg.conf when I am trying to sort out console resolution (X doesn't even need to be running)?
did you not say that grub loads in the correct resolution and then x switches to a lower resolution? having looked at your xorg.conf, there's not much info for your card and monitor in there so it seems to me it's an x issue and not grub.

---

### Post by miromiro on 2010-01-27
No - grub loads at correct resolution 1680x1050(as does X), but if I switch to TTY1-6 it displays at 1280x1060 - so the console resolution doesn't appear to persist beyond grub...

---

### Post by Leppie on 2010-01-27
> **miromiro said:**
> No - grub loads at correct resolution 1680x1050(as does X), but if I switch to TTY1-6 it displays at 1280x1060 - so the console resolution doesn't appear to persist beyond grub...
i'm not sure which resolutions you are using, i've never seen 1280x1060, nor 1680x1050
anyways, using the vga= kernel option you can set the frame buffer mode.
i don't know the one for your card, but i found a nvidia code of  0x0369 for that resolution
so open your grub defaults file with an editor:
```
gksudo gedit /etc/default/grub
```
and change the following line to something like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="ro quiet splash vga=0x0369"
```
of course [COLOR=Red]***you will have to check***[/COLOR] the resolution and the matching frame buffer code.

then run update-grub:
```
sudo update-grub
```

---

### Post by miromiro on 2010-01-27
Thanks Leppie - that is the correct code (i was using it in my kernel line for versions up to 9.04).

My understanding was that "vga=xxxx" was deprecated in Grub2 and we weren't supposed to use it anymore: so is this a "hack" to get around that?

In any event, I'll try it this evening and see how it goes...

---

### Post by Leppie on 2010-01-27
> **miromiro said:**
> Thanks Leppie - that is the correct code (i was using it in my kernel line for versions up to 9.04).

My understanding was that "vga=xxxx" was deprecated in Grub2 and we weren't supposed to use it anymore: so is this a "hack" to get around that?

In any event, I'll try it this evening and see how it goes...
i'm not sure, i don't have a nvidia card (so no "strange" resolutions).
just try it, if it doesn't work remove it from the kernel options.

---

### Post by aznranndydraman on 2010-01-28
Sorry guys, I've been really busy, but I've follow the thread from time to time.

> **Leppie said:**
> i'm not sure, i don't have a nvidia card (so no "strange" resolutions).
just try it, if it doesn't work remove it from the kernel options.

the vga kernel command is deprecated for grub2. I have tried it and ubuntu just boots like it isn't there.

This also brings us back to the first post in this thread, where I mentioned the role of fbcon and vesafb in booting with grub2 - people from most forums report getting the desired console resolution only with the ...payload=keep or whatever, does that mean somehow grub2 is able to replace fbcon (seems like it because grub2's resolution is right), did it interact with the ttys?

When I have time I would want to try some combinations of working with/without the kernel modules, of course someone who has the time can try that and we'll appreciate it very much.

---

### Post by miromiro on 2010-01-28
I can confirm adding the vga value to the GRUB_CMD_LINE has no effect - resolution is still very low.

For reference, my full /etc/default/grub:
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="ro quiet splash vga=0x0369"
GRUB_CMDLINE_LINUX="gfxpayload=true"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050x24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by miromiro on 2010-01-28
SOLVED
This post has the secret ingredient:
[http://newyork.ubuntuforums.org/showpost.php?p=8632103&postcount=8](http://newyork.ubuntuforums.org/showpost.php?p=8632103&postcount=8)

The key is to use the vga value PLUS changing the entries in /etc/grub.d/10_linux from linux and initrd to **linux16** and **initrd16**

w00t!:D

---

### Post by Leppie on 2010-01-28
> **miromiro said:**
> SOLVED
This post has the secret ingredient:
[http://newyork.ubuntuforums.org/showpost.php?p=8632103&postcount=8](http://newyork.ubuntuforums.org/showpost.php?p=8632103&postcount=8)

The key is to use the vga value PLUS changing the entries in /etc/grub.d/10_linux from linux and initrd to **linux16** and **initrd16**

w00t!:D
out of curiosity, do you happen to know what these 2 options do exactly?

---

### Post by miromiro on 2010-01-28
Apparently, there is a bug with memdisk using 32bit boot protocol - so it forces 16...

[http://old.nabble.com/-bug--27621--Unable-to-load-simple-boot-manager-%28SBM%29-with-Grub-2-td25779369.html](http://old.nabble.com/-bug--27621--Unable-to-load-simple-boot-manager-%28SBM%29-with-Grub-2-td25779369.html)

---

### Post by Leppie on 2010-01-28
> **miromiro said:**
> Apparently, there is a bug with memdisk using 32bit boot protocol - so it forces 16...

[http://old.nabble.com/-bug--27621--Unable-to-load-simple-boot-manager-%28SBM%29-with-Grub-2-td25779369.html](http://old.nabble.com/-bug--27621--Unable-to-load-simple-boot-manager-%28SBM%29-with-Grub-2-td25779369.html)
ok, hadn't understood you're using memdisk.

---

### Post by pbrane on 2010-01-28
> **Leppie said:**
> try the following:
```
set gfxpayload=XXX  ##replace with the desired resolution + color depth. e.g.: 1024x768x32
```

That doesn't work for me. My understanding is that it doesn't work for grub2 on ubuntu 9.10 at all. Some issue about the framebuffer. The only way I've been able to set my VT resolution is by using the deprecated vga=xxx.

The memdisk issue isn't the problem for me. Although I will try using gfxpayload with init16 just to see what happens. But Everything I've found has this being a framebuffer issue and ubuntu.

---

