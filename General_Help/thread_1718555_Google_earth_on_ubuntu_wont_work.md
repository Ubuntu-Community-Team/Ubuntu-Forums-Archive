---
title: "Google earth on ubuntu wont work"
date: 2011-03-31
forum: General Help
---

### Post by mrpenguin on 2011-03-31
Why am I having so much issues installing Google Earth on Ubuntu 10.10 but on Linux Mint 10 it installed with one click ?

Is Linux mint and Ubuntu pretty much not the same thing ??

I have tried all different ways of installing google earth that I was able to find on the internet but no luck.


What is so different in Linux Mint 10 that makes it work with one click ??

---

### Post by falko on 2011-03-31
Please try this: [http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10](http://www.howtoforge.com/how-to-install-google-earth-on-ubuntu-10.10)

---

### Post by Lenny212 on 2011-04-01
Didn't work for me.

When I typed:
sudo make-googleearth-package --force
I got many, many error messages similar to this:
dpkg-shlibdeps: warning: Can't extract name and version from library name `libbase.so'

It then said:
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: building package `googleearth' in `./googleearth_6.0.2.2074+0.5.7-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb

I then entered:
sudo apt-get install gdebi-core
and:
sudo gdebi -i googleearth_6.0.2.2074+0.5.7-1_i386.deb

I can see GoogleEarth icon in applications menu. Clicking this results in no activity at all. Have checked System Monitor and there is no evidence of GoogleEarth here.
Strange!

---

### Post by beew on 2011-04-01
Install lsb-core from Synaptic. Then download the .deb file from googleearth.

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Right click and that's it.

Mint probably has lsb-core preinstalled.

---

### Post by mrpenguin on 2011-04-01
Thanks I have it working finally

Still wondering why its so easy with Linux Mint ???

---

### Post by Lenny212 on 2011-04-03
Thanks beew - works just fine

---

### Post by haudace on 2011-04-03
SOLVED. Fixed issue described below with upgrade to 11.04 natty. Edit on May 3rd 2011.

---------------------------------------------------------------------------------------

Just installing lsb-core might not fix all your problems. Google earth website (system requirements section) mentions LSB package is required for full functionality.[INDENT] Side note:  Anybody noticed the website misleads linux users by claiming Linux distros installs LSB dependency automatically? Check attached image.
[/INDENT][CENTER]----------------

[/CENTER]
Anyways, I am stuck at the moment with this new problem. Every time I zoom in on a area, the map image doesn't seem to be rendered/generated properly. Some threads have suggested there's a compatibility issue with compiz. It looks like everything else is A-OK though as evidenced by the picture (I can search directions for instance, just the map is not very... eye candy hehe).

Graphic card: 
> *-display               
       description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:d0000000-dfffffff memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffffFrankly, I am lost. Any input, however small, will be appreciated.

Haudace.

---

