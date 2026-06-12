---
title: "X.org freeze"
date: 2005-01-30
forum: General Help
---

### Post by MalteL on 2005-01-30
Hello,

I've got Ubuntu installed on my computer for about a week, and I quite 
like it. But my X.org seems to malfunction. 

When i first installed Ubuntu (Warty), XFree wouldn't even start. It just 
showed me some blurry colors (like a television, that can't get a proper 
signal). I could, however, boot in recovery mode, and through the command 
line apt-get the Nvidia drivers. Then I rebooted, and XFree told me that 
it wasn't configured. I reconfigured it with 
dkpg --reconfigure xserver-xfree, but it still showed the same error message.

So i installed Hoary and X.org. X.org worked fine at first sight, but 
after a few minutes of Firefoxing, it freezed, and I had to reboot. It freezes os often, that i it's hard for me to use my computer. The freezes can happen in one of the following ways:

1) It freezes, and won't update the screen at all.

2) It partially freezes. I can move my mouse around, but i can't click at anything. My keyboard doesn't work.

I've googled around, and it looks like I am not the only one who have the problem. The only one who solved the problem, however, was a guy in this forum. Here's the thread: [http://ubuntuforums.org/showthread.php?t=4035](http://ubuntuforums.org/showthread.php?t=4035)
Notice that the bug was not exactly the same (he couldn't even move his mouse).
Adding XaaNoSolidFillRect to my xorg.conf, however, did not change anything.

I hope you can help me, since I can't really use my computer normally.

Thanks in advance,
Malte

---

### Post by MalteL on 2005-02-04
Please help me!
This is quite a problem, as I can't really use my computer, and I really don't want to switch back to SuSE!

Thank you,
Malte

---

### Post by subjectdenied on 2005-02-04
hi,

try to press the "e"-key twice in grub when booting on the line that actually boots your kernel.

add

<code>pci=noacpi</code>

to it, press enter and press "b"

this disables the power-options, which didn't work with my combination of motherboard and nvidia graphiccard

hope this helps

---

### Post by MalteL on 2005-02-07
Thank you for your help.

It does, however, not seem to work.
For various reasons, I couldn't enter what you said at the prompt. But I found the file /boot/grub/menu.lst, and it seems that it is where GRUB stores it's information, so I edited that. I changed
```
title   Ubuntu, kernel 2.6.10-2-amd64-generic Default
root   (hd0,0)
... More geeky stuff here ...
```
to
```
title   Ubuntu, kernel 2.6.10-2-amd64-generic Default
root   (hd0,0) pci=noacpi
... More geeky stuff here ...
```

Would that work?

Thank you very much,
Malte

---

### Post by friez on 2005-02-07
no you have to put it here ```

title   Ubuntu, kernel 2.6.10-2-amd64-generic Default
root   (hd0,0)
 kernel /vmlinuz-2.6.10-lxnay3 ro <---- after here   init=linuxrc root=/dev/hdh2 video=vesa-tng:ywarp,mtrr,1280x1024-32@60 splash=silent theme:emergence
```

---

### Post by MalteL on 2005-02-11
Okay... I tried what you said, but it is not working.
But I found something interesting when looking in /var/log/Xorg.0.log:
```

[...]
(WW) NVIDIA(0): Option "XaaNoSolidFillRect" is not used
(WW) NVIDIA(0): Option "XaaNoScanlineCPUToScreenExpandFill" is not used
(WW) NVIDIA(0): Option "XaaNoScanlineImageRect" is not used
(WW) NVIDIA(0): Option "XaaNoPixmapCache" is not used
(WW) NVIDIA(0): Option "XaaNoScreenToScreenCopy" is not used
[...]

```

Does anyone know why they are not used?

Thank you,
Malte

---

### Post by friez on 2005-02-12
what graphics card / mb due you have
when using the nvidia driver did ou comment out dri  in xorg.conf
type  dmesg in the tem and see what is prints out ```
dmesg | less
``` post any error  here :|

---

### Post by MalteL on 2005-02-20
Okay, now it only freezes when I use Firefox or a media-application (Totem, for example). It might be because I commented out DRI, haven't tested the reason. It's interresting, that the freezes will occur random (and much more often), if I turn Composite _off_. As for the graphic card, I am an idiot at remembering hardware specs, so I can't answer it - do you now if there are any ways to check that? Lastly, right now I'm not at my Linux-box, so I can't check dmesg. Will do as soon as possibly.

Cheers,
Malte

---

### Post by streetbmx on 2005-02-27
I've experienced similar symptoms. It may be the gam server kernel panic?

[http://ubuntuforums.org/showthread.php?t=15513&highlight=gam](http://ubuntuforums.org/showthread.php?t=15513&highlight=gam)

---

### Post by MalteL on 2005-03-04
Yup - It WORKS!!!

Really - it runs perfectly!
I don't know how I fixed it, but now it works. Here's what I did:

1) In a moment of superstition I reinstalled Ubuntu. Not suprisingly, it couldn't start X

2) Upgraded to Hoary, installed X.org and choosed that as my default Xserver.

3) Rebooted. WAI! It worked!

But it doesn't run X.org:

```

ml@ubuntu:~ $ ps -auxc | grep X
3808  3.9 10.4 134416 53036 ?        SL   19:09   3:01 XFree86
ml@ubuntu:~ $ file /etc/X11/
/etc/X11/: directory
ml@ubuntu:~ $ file /etc/X11/X
X                 Xresources/       Xsession.d/       Xwrapper.config
XF86Config-4      Xsession          Xsession.options
ml@ubuntu:~ $ file /etc/X11/X
/etc/X11/X: symbolic link to `/usr/bin/X11/XFree86'

```
But I don't care - as long as it works, it's fine with me.

Thank to all of you, for spending you're time helping me.

Cheers,
Malte

---

