---
title: "xorg.conf in new xorg version"
date: 2011-01-28
forum: General Help
---

### Post by J V on 2011-01-28
There's no more xorg.conf in newer xorg versions, so how do I input a manual display resolution? (Stupid regressions)

---

### Post by Grenage on 2011-01-28
You can create one *if* you need one, and it will be used.

---

### Post by J V on 2011-01-28
Ok, is there any way to get a default? (Any command to create a current Xorg.conf that won't mess everything up?)

---

### Post by Grenage on 2011-01-28
I believe that this will create a standard static output, but I've not used it myself:

```
sudo Xorg -configure
```

---

### Post by J V on 2011-01-28
Every time I try to run that from a tty it says it can't because xorg is still running, and every time I try to kill gdm it starts up again. chroot from live disc isn't an option, this is an old machine incapable of running a live disc or usb. (The installation was needless to say a nightmare)

---

### Post by anglican on 2011-01-28
> **J V said:**
> Every time I try to run that from a tty it says it can't because xorg is still running, and every time I try to kill gdm it starts up again. chroot from live disc isn't an option, this is an old machine incapable of running a live disc or usb. (The installation was needless to say a nightmare)Boot into recovery mode and run ```
sudo Xorg -configure
```there.

H

---

### Post by J V on 2011-01-28
It won't boot into recovery mode either. Crashes at "Creating slab <bio-0> at 0"

It's a VERY old computer (on crunchbang)

Would there be a way to just disable gdm from constantly starting up then get the config file and reset it?

Also, the tty is also at a lower resolution than the screen is capable of, is it possible this problem has a different cause?

---

### Post by clhsharky on 2011-01-28
J V

Whats your video chip?

Sharky

---

### Post by Grenage on 2011-01-28
You can get to a low run level with Ctrl-alt-F1; login, then:

```
sudo /etc/init.d/gdm stop
```

Then run the xorg command.

---

### Post by J V on 2011-01-28
> **Grenage said:**
> You can get to a low run level with Ctrl-alt-F1; login, then:

```
sudo /etc/init.d/gdm stop
```Then run the xorg command.Worked! Messing with xorg.conf now...

As for the video card, crunchbang statler doesn't have lshw (I have no idea why) but lspci says "VGA compatible controller: Intel corporation 82815 Chipset Graphics Controller (CGC)"

I was going to install lshw but this old laptop doesn't have ethernet and I haven't managed to get keryx working yet.

Ok, tried that, editting xorg.conf still doesn't work. Must be a driver issue...

---

### Post by Grenage on 2011-01-28
The Intel drivers are normally very good.  Are you just unable to change resolutions, or are there other problems?

---

### Post by J V on 2011-01-28
I can change resolution, but it's stuck at maximum a lower than optimal resolution creating a large black border around the screen.

The latptop is very old, I had to disable acpi in the boot options (acpi=off) and couldn't get the live disc to work (Text install worked though) because the disc drive is dodgy.

In addition, there are no drivers for the pcmia slots so the ethernet card won't work and I can't get direct internet connection with it.

The laptop was made in the 90s (Or 2k, idr) when intel drivers were probably not as good as they are now.

Right now all I care about is getting the display to function correctly.

Yes it's a ridiculously old laptop but it seems to work fine with crunchbang.

---

### Post by Grenage on 2011-01-28
Plenty of old machines are still useful!

You could try adding a modeline; I have a rough guide [here]("http://www.grenage.com/xorg.html").  Failing that, post your laptop model and desired res, and I can give you one to try.

---

### Post by J V on 2011-01-28
Yes the mode line was how I tried it but after reboot it still doesn't show up as an option in grandr

---

