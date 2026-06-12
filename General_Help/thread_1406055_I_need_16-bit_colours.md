---
title: "I need 16-bit colours"
date: 2010-02-13
forum: General Help
---

### Post by Bright Carver on 2010-02-13
Hi

I'm running Karmic on a IBM Thinkpad 390X with 128Mb RAM.

It's capable of 32 bit colour so Karmic installed fine with that setting, however my acceleration runs best at 16 bit, so I need to change it down.

After searching forums, I think I have to edit xorg.conf but I can't find it in any of the locations and I'm not sure exactly how to create it or if I'll break something if I create it wrong.

Can anyone help?

Cheers,

Karl

---

### Post by audiomick on 2010-02-13
Hi.
9.10 Karmic does not have an xorg.conf file by default, which will be why you can't find it. It is still created by some graphics drivers, for instance the nVidia settings utility, and will be used if present.

If you create one wrong, I think you do run the danger of messing things up.

As far as I know, the new mechanism is randr, but I am not too sure about it. I haven't had to look into it yet.

---

### Post by Bright Carver on 2010-02-13
I've checked, and yes indeed, xrandr is on my system.  I've checked the thinkwiki and other places for xrandr but haven't found any way of altering colour depth.

Can you recommend an Ubuntu packaged frontend for xrandr that includes colour depth in it's options?

Thanks

Karl

---

### Post by flippo on 2010-02-13
I believe you can auto-generate xorg with ```
dpkg-reconfigure xorg-server
```  I'm not entirely sure how to set the depth to 16 bits, but my configuration (for 24 bits) is:
```
Depth "24"
```
in the "Device" section and:
```
DefaultDepth "24"
```
in the "Screen" section.

You should change those numbers to 16, although I would recommend reading the xorg documentation and understanding what your doing before editing xorg.conf.

EDIT: Sorry, was just behind your post.  This is to configure your X server directly, I'm not entirely sure what xrandr does.

---

### Post by Bright Carver on 2010-02-13
Hi, thanks for replying :)

I ran the command but it tells me xorg-server is not installed.  Is it perhaps called something else?

Karl

---

### Post by flippo on 2010-02-13
Hmmm, that may be an outdated method now, I don't run 9.10, so I couldn't test it.  Try running:

```
Xorg -configure
```

and moving the result to /etc/X11/xorg.conf

---

### Post by Bright Carver on 2010-02-13
OK, that didn't work either.  It says "fatal server error".  I thought it was because I was in X and it needed to be shut down to be configured but I couldn't find a way of getting out of X.  Logging off and logging in as terminal session just gives the same answer after a bunch of stuff that scrolls past too quick.

It's honestly just the colour depth I need to change.  Why is this so hard?

---

### Post by flippo on 2010-02-13
Working with Xorg can be a pain when your not used to it.  Ubuntu tries to abstract it away as much as possible.  To close your X server go to tty1 (ctrl+alt+f1) then log in and type ```
sudo /etc/init.d/gdm stop
```
Then to restart it type```
sudo /etc/init.d/gdm start
```Once you've stopped gdm you will be able to ```
sudo Xorg -configure
``` I hope.  Keep me updated with any issues.

---

### Post by flippo on 2010-02-13
Also, when gdm is running, to return to your X session hit (ctrl+alt+f7).

---

### Post by mhgsys on 2010-02-13
> Hi, thanks for replying

I ran the command but it tells me xorg-server is not installed. Is it perhaps called something else?

Karl

@Flippo & Bright Carver ; the command ```
dpkg-reconfigure xorg-server
```

Should in fact be;


```
sudo dpkg-reconfigure xserver-xorg
```


@Bright Carver, hope this helps you out.
;)

---

### Post by Bright Carver on 2010-02-13
Yeah, I figured it would be sudo, forgot to mention that was what I tried :)

Anyway, tried Ctrl+Alt+F1 and my screen changed into a mess of flashing colours so I had to Ctrl+Alt+F7 back again.  It's similar to the mess I get when I've just shut down the laptop (because Ubuntu doesn't know how to switch it off properly) and when XFCE is loading the little mouse turns all weird and blocky for a couple of seconds.

Thanks for taking the time :)

Karl

---

### Post by mhgsys on 2010-02-13
there was more then just the missing sudo; the entire command was faulty

 xorg-server

is not the same as 

 xserver-xorg

---

### Post by mhgsys on 2010-02-13
Ehhhr,.... WAIT!

XFCE you say>?


well my friend; then sudo start /etc/init.d/gdm won't help you I believe; for that is meant for gdm.

```
sudo /etc/init.d/xdm start
``` 

should work for you

edit; same go's for stop ofcourse

---

### Post by Bright Carver on 2010-02-13
Hi, thanks for helping all :)

Ok, I can't get into tty mode because my computer doesn't like switching without a screenful of colour mess.  Well, when I hit Ctrl+Alt+F1 it splurges but still lets me  Ctrl+Alt+F7 back again so I presume it's still working underneath, I just can't see what I'm typing...

By running the corrected xserver command (sorry) it asked for pass then went back to command line without seemingly doing anything.  Was I supposed to add the 16-bit settings as parameters or switches to the command?

Sorry for the ignorance, I had assumed this would be a simple matter but nothing seems to be working...

Thanks,

Karl

---

### Post by mhgsys on 2010-02-13
Well, actually it's still a simple matter of editing the xorg.conf file change te color depth and restarting xdm.

2 bad your screen gets messed up when you switch to console; 

there is in fact another way I belive; 

When booting up , at the grub menu choose recovery mode; select; root......Drop to root shell prompt

The console will hopefully work without the color mess, since you don't need to switch to it from xdm.

anyway;

in the prompt type;
```
nano /etc/X11/xorg.conf
```

and adjust your color depth

if the file is not there; auto-generate it with 
```
dpkg-reconfigure xserver-xorg
```

adjust it; save it; reboot
(I'm not sure /etc/init.d/xdm can be started from root console, that's why the reboot)

*notice;  now the sudo command would be irrelevant since your already in a root console

---

### Post by jocko on 2010-02-13
> **Bright Carver said:**
> By running the corrected xserver command (sorry) it asked for pass then went back to command line without seemingly doing anything.  Was I supposed to add the 16-bit settings as parameters or switches to the command?
dpkg-reconfigure does not make a xorg.conf, since xorg.conf is not part of the xserver-xorg package anymore... So if you really need one, you need to make it in another way.
One way is to boot into recovery mode and run:
```
Xorg -configure
mv /root/xorg.conf.new /etc/X11/xorg.conf
```
Then edit it to your need with:
```
nano /etc/X11/xorg.conf
```

---

### Post by Bright Carver on 2010-02-14
Thanks for letting me know.

If xorg.conf is not part of xserver-xorg anymore, is there a new way to configure for 16-bit colour depth, or should I go with creating the xorg.conf file because that was the only way?

(I'm perfectly comfortable working in command mode, I did a bit of Unix admin at college years ago!)

Thanks for all the help :)

Karl

---

### Post by audiomick on 2010-02-14
> **Bright Carver said:**
> Thanks for letting me know.

If xorg.conf is not part of xserver-xorg anymore,
I would put that differently, for the sake of splitting hairs ;)
The file xorg.conf is still part of xserver-xorg, but there is a new process being implemented that makes it obselete.

 > is there a new way to configure for 16-bit colour depth, or should I go with creating the xorg.conf file because that was the only way?
I dare say there is a new way, but I have not had much success trying to find info about the whole xrandr business. I would say, if you are able to create an xorg.conf that works, do that. The file has not completely been phased out yet. The nVidia drivers, for instance, still write and use one.

---

### Post by jocko on 2010-02-14
> **audiomick said:**
> I would put that differently, for the sake of splitting hairs ;)
The file xorg.conf is still part of xserver-xorg, but there is a new process being implemented that makes it obselete.
Let's split some more hairs, as what you say is not correct:
xorg.conf is *not* part of **xserver-xorg** (the package) anymore, but if it exists, **Xorg** (the x server) will use it.
dpkg-reconfigure just re-runs the configuration scripts from the package the same way as when the package was first installed, and as the package no longer provides the script that generates a xorg.conf, dpkg-reconfigure will not make one.

Unfortunately I don't think there is any way of changing the color depth with xrandr, so I think a xorg.conf is really needed for this...

---

