---
title: "Should I still Install???"
date: 2006-06-24
forum: General Help
---

### Post by charles.g.moore on 2006-06-24
I tried to install Kubuntu 6 but I was having a problem installing from the live DVD,

I'm pretty sure it's a video prob. so I downloaded the DVD version and got the same results, the second time I booted into Kubuntu DVD using safe graphics mode it WORKED!!!

So now im wondering if I should go ahead and install now while in safe graphics mode or wait

 because I have seen alot of posts with people experiencing the same prob as i was.

Is there a way to disable my video card and just use the default???  If so can someone tell me how?

Thanks 
Chuck

---

### Post by taurus on 2006-06-24
You can try to install Dapper with the alternate version!!!  It uses the old ncurse base.  Otherwise, you can go for the server version and install either Gnome, KDE, or XFce4 window manager after that...
```

sudo apt-get install ubuntu-desktop <-- for Gnome
sudo apt-get install kubuntu-desktop <-- for KDE
sudo apt-get install xubuntu-desktop <-- for XFce4

```
What kind of video card do you have anyway?

---

### Post by charles.g.moore on 2006-06-24
Sorry it's a radeon 9600 Por (I think, I know its a Radeon 9600)

Would the alternate version stabilize the video problem?

Once I do the sudo apt-get install kubuntu-desktop do I just follow the instructions?

As you can see Im a windows sucker trying to convert...

---

### Post by Ramses de Norre on 2006-06-24
I had problems when I first installed breezy with my ati x600 too, everything frooze.. I think the alternate installation or installation from save graphics mode should work fine, but you'll need to change the driver for your videocard to vesa from terminal, install fglrx and set fglrx as driver in order to get it working.
This will only work when you've got the same problem I had..

---

### Post by vigleik on 2006-06-24
I've installed from safe mode and changed my screen resolution later, and there's no good reason why that shouldn't work. I have a nvidia card instead of ati, but I think the following procedure should work:

1. Install from safe mode.
2. Install goodies with easyubuntu, including the ati driver.
3. "sudo dpkg-reconfigure xserver-xorg". Choose the ati driver and the resolutions you want, give the default answer to everything else.

Vigleik

---

### Post by Patrick-Ruff on 2006-06-25
yes, live-cds generally do have weird errors like that, but the thing is, after you install it there is a wide array of things you can do to fix whatever may *really* exist.


good luck

---

