---
title: "Need help with Radeon HD5450 drivers in Ubuntu."
date: 2011-01-24
forum: General Help
---

### Post by MewTech on 2011-01-24
Sorry guys, this is my first time on this forum. Don't know the right place for this.

Long time Ubuntu user, I can always find ways around my problems, until recently.

Every time I do a fresh install of Ubuntu, the first two things I install are wireless and my video card drivers.
I always did System - Administration - Additonal Drivers to install the drivers my video card needed. Until I learned that ATI actually has drivers on their site for Linux.

It came in a 119 meg .run file. So, naturally, I edited the permissions and checked "make executable", then ran it in terminal.

Everything works fine, says it installs fine. And that it's in standard configuration. So I did a reboot to let everything load fresh, but, uh oh. Ubuntu boots up to the command line.

Now the only time I can get any display is when I boot up into failsafe graphics mode....any ideas?

Sorry for the long post.

~MewTech

---

### Post by slooksterpsv on 2011-01-24
I've had hit and miss luck with the drivers off of AMD, no offense I love AMD I love  their graphics, but the fglrx drivers do work better IMO.

Try this, at the terminal, run:
```

sudo aticonfig --initial -f

```

Then reboot, this will generate an xorg.conf file for your system.

---

### Post by MewTech on 2011-01-24
> **slooksterpsv said:**
> I've had hit and miss luck with the drivers off of AMD, no offense I love AMD I love  their graphics, but the fglrx drivers do work better IMO.

Try this, at the terminal, run:
```

sudo aticonfig --initial -f

```Then reboot, this will generate an xorg.conf file for your system.

That says it creates a file, but upon reboot I'm greeted with a straight black screen instead of the command line.

Contents of xorg.conf (from failsafe)
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

Also, on that note. What are the differences between the drivers in System - Administration -Additional Drivers, and the ones on ATI's site? They both use the word "proprietary"

---

### Post by tcrapper on 2011-01-24
The ones from Ubuntu are probably older. The recommended way to install the ATI driver on ubuntu systems, is by telling the installer to create debian packages. Otherwise you might mess your system up.

You might want to reinstall, if you didn't install the drivers the correct way.

Remove the old driver first.

```
sudo apt-get remove fglrx fglrx-amdcccle
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -fr /usr/lib/fglrx
sudo rm -fr /etc/ati
sudo reboot
```

I use the install-fglrx-debian.sh from kanotix.com.

Click ctrl alt f1, then run the below.

```
wget [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)
chmod 755 install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh -z
sudo aticonfig -f --initial
sudo reboot
```

Or you can do the other method [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package) there.

The install-fglrx-debian.sh shell script should hopefully remove a bad installation of the ATI driver though.

---

### Post by MewTech on 2011-01-24
> **tcrapper said:**
> The ones from Ubuntu are probably older. The recommended way to install the ATI driver on ubuntu systems, is by telling the installer to create debian packages. Otherwise you might mess your system up.

You might want to reinstall, if you didn't install the drivers the correct way.

Remove the old driver first.

```
sudo apt-get remove fglrx fglrx-amdcccle
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo rm -fr /usr/lib/fglrx
sudo rm -fr /etc/ati
sudo reboot
```I use the install-fglrx-debian.sh from kanotix.com.

Click ctrl alt f1, then run the below.

```
wget [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)
chmod 755 install-fglrx-debian.sh
sudo ./install-fglrx-debian.sh -z
sudo aticonfig -f --initial
sudo reboot
```Or you can do the other method [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package) there.

The install-fglrx-debian.sh shell script should hopefully remove a bad installation of the ATI driver though.
That first .sh script has been downloading stuff for almost half an hour, should it be doing that?

---

