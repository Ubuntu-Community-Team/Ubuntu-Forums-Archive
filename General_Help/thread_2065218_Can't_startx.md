---
title: "Can't startx"
date: 2012-10-01
forum: General Help
---

### Post by mathiflip on 2012-10-01
Hi,

I'm really desperate because It seems I've tried everything and I just googled another 4 hours without a result.

A time ago I booted up in ubuntu (dualboot laptop with win7 and Ubuntu 12.04) And I always got in the tty1.

Couldn't startx, gives error:
```
Fatal server error: no screens found
```

So I tried regular stuff like replacing xorg.conf with xorg.conf.backup, updating & upgrading,...

When I go to ctrl+alt+F7 I can see 1 process failing: 
```
Starting load fallback graphics devices [fail]
```

I googled on that but no luck

things I tried:

updating
apt-get install -f
dpkg --configure -a
dpkg-reconfigure xserver-xorg
reinstall nvidia-current (but says its already the latest version)

Nothing worked! After dpkg-reconfig I copied the xorg.conf.new to /etc/X11/xorg.conf but still no luck.
Got the same errors when starting X or rebooting.

I also found an error in the Xorg.log about vesa:
```
Error inserting vesafb
and
vesa: ignoring devices with abound kernel driver
```

If I google on this errors I still can't find a solution.

Finally I found this
```
http://askubuntu.com/questions/167000/xorg-server-configuration-fail-no-screens-detected
```
But removing monitors.xml didn't fix the problem.


So as you can see I tried a lot but still no solution. I'm getting desperate. Hope someone can help me further.
What am I missing?


and output of lspci | grep -i vga is:
```
VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 320M] (rev a2)
```

---

### Post by dargaud on 2012-10-01
Classic NVidia driver problem. Do you know if you were using the official binary NVidia driver or the Nouveau driver ?
If the former, see if you already have the installer, it's called NVIDIA-Linux-.... If not, download it (use links or lynx in text mode like at the time of the dinosaurs). Then run:
```
$ sudo ./NV[tab] --update
```
Press OK everywhere, then do:
```
$ sudo /sbin/init 5
```

If you were using the Nouveau driver, personally I blacklisted it so I could use the binary driver, but maybe someone else wants to chip in...

---

### Post by mathiflip on 2012-10-02
thanks for the reply, but I can't find out how to do your steps.

I removed hte nouveau drivers, I did a remove of nvidia-current and installed it again and enabled it with jockey-text.

But still no changes.

---

### Post by dino99 on 2012-10-02
Nowadays X is directly drived by the kernel, so xorg.conf is not needed and often brings sad effects if its not correctly set. Thats said, remove it.

I suppose you have booted into recovery mode, to check and repair broken package(s). It seems to me you might miss a xorg package. Have you removed ubuntu-desktop and made partial upgrade(s) ? or forced package(s) installation ?

---

