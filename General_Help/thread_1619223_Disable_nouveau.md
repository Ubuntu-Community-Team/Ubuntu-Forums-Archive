---
title: "Disable nouveau"
date: 2010-11-11
forum: General Help
---

### Post by milton666 on 2010-11-11
Hey everyone, I just re-installed  Ubuntu after awhile of trying out some different distros. After my fresh install I downloaded the NVIDIA driver for my graphics card and of course got the business about how it can't be installed alongside nouveau. So I disabled nouveau for one boot by holding shift during boot and adding nouveau.modset=0 to the kernel line then installed the NVIDIA driver. Problem now is though every time I restart my comp if I don't go to the grubs menu and disable nouveau it tries to start alongside the NVIDIA driver and my computer won't boot. I know It's possible to permanently disable nouveau because I did it when I had Linux Mint installed, but I can't figure it out in Ubuntu.

I am EXTREMELY NEW to Linux so although I do appreciate any help that anyone gives, it won't really be any help at all unless you can give me detailed, step by step instructions. I have really enjoyed the switch to Linux over the last few months and everyone is really helpful, but their help is usually so cryptic and assumes that you already know a great deal about Linux that it's too hard to follow. Basically, talk to me like I'm a child, lol.

Thanks ahead for any help.

---

### Post by milton666 on 2010-11-11
b

---

### Post by bmeakings on 2010-11-11
You can edit the modprobe blacklist file (terminal: gksu gedit /etc/modprobe.d/blacklist.conf) and add these entries at the bottom:

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Then reboot and they shouldn't be loaded. I had to do the same with my system.

---

### Post by auh2o on 2010-11-22
bmeakings, that didn't work for me. I did that AND let the nvidia installer create the /etc/modprobe.d/nvidia-installer-disable-nouveau.conf file, but the installer still says I have nouveau installed. I also removed the xorg.conf file (which had nvidia set as driver anyway).

I suppose you could permanently add the nouveau.modset=0 string to grub. What else is there to do that I've overlooked?

---

### Post by auh2o on 2010-11-23
Forget it; problem solved.

---

### Post by ThomWilhelm on 2010-12-01
Can you let me know how as I have the same issue :p

---

### Post by gian666 on 2010-12-13
I had the same (quite dramatic) problem (i will describe it with some detail, and then write ho I solved it)

1. tried to use the external monitor connector of my perfectly functioning DELL Latitude E6410 using nvidia driver... does not work (i.e. the external monitor does not see in any way the PC)

2. using the Restricted Driver dialog (in the menu "Administration") I uninstall the nvidia drivers (I actually thought it was a "disable"... but in practice it is a full uninstall) and reboot

3. all seems fine, and as I plug the external monitor (a projector) the LCD goes dark and the projector starts to work... unfortunately the resolution is ridiculously low, so I decide to remove the projector cable.

4. As I remove the projector cable, the E6410 lcd screen flickers but does not retro illuminate !! (i.e. I can see a faint picture)

5. I reboot, hoping it was just a transient problem: NO LUCK, the screen is pitch black, not even the faintest image.

after some trial and error (about 3h !!! :mad: !!!) I managed to get at least a console (By pressing F2 continuously while booting the "safe mode" version of the kernel) don't know if it is the most efficient way....

from the console (and using a cable, since wifi did not work either) I reinstalled nvidia drivers and stuff.... reboot.... still no luck, apt-get --reinstall .... no luck etc etc

the solution.... I put "nvidia" manually in xorg.conf, and got at least a low-res X.
Obviously, being low rez, no menues where visible (went somewhere off screen, I believe) and had to manually start the restricted driver dialog whose name is jockey-gtk and reactivated the normal nvidia driver from nvidia....

After doing all this I realized there is also a text only version of the Restricted-driver dialog (/usr/bin/jockey-text) ... probably this could have saved me quite some time.... unfortunately, after hours of ubuntu forum browsing, I did not found anyone talking about jockey.


A final comment: the nouveau driver, for my laptop, is currently more a virus :biggrin: than a driver.

---

### Post by mtxelectronics on 2011-01-06
> **bmeakings said:**
> You can edit the modprobe blacklist file (terminal: gksu gedit /etc/modprobe.d/blacklist.conf) and add these entries at the bottom:

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Then reboot and they shouldn't be loaded. I had to do the same with my system.

You also have to type "sudo update-initramfs -u" to create a new image and reboot before nouveau is actually removed.

---

