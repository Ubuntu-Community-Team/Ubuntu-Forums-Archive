---
title: "Can't start Xwindow on ATI Radeon Xpress 200M"
date: 2006-05-06
forum: General Help
---

### Post by baosheng on 2006-05-06
I have tried Ubuntu 5.10 both install CD or Live CD. NONE of them can start xwindows on my ThinkPad R51e-2XC whose graphic card is ATI Radeon Xpress 200M. 
Another friend of mine has a HP ze2502 laptop using the same graphic card.
He also has the problem as me.
 Can any one help me ?

---

### Post by Fass on 2006-05-06
Tried running

sudo dpkg-reconfigure xserver-xorg

And choosing the "vesa" driver? That should let you start X. After that, you should follow one of the guides on this forum to install the fglrx driver. The native xorg "ati" driver has never worked well for me.

---

### Post by baosheng on 2006-05-06
I have choosed vesa and screen(1024x768@60hz).
But after I typed startx, it says 
[FONT="Arial Narrow"](EE) VESA(0): No matching modes
(EE) Screen(s) found, but non have a usable configuration.[/FONT]

---

### Post by pr0phet1024 on 2006-05-08
Exactly the same problem here! has anyone found a fix for this?

---

### Post by sublime on 2006-05-08
im using the same card on my compaq.  in command more run:

```


sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #select the "vesa" module

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run
(this will download the ati driver from the ati website)

sudo apt-get install gcc-3.4 module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
cd directory of ati driver
chmod +x ati-driver-installer-8.24.8-x86.run
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb

sudo rm /usr/src/fglrx-kernel*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

reboot

```

this was taken from the walk through on [http://wiki.cchtml.com](http://wiki.cchtml.com)

---

### Post by zerofx on 2006-05-15
I had the same problem when I attempted to install Ubuntu also, and the same problem when I attempted to install Fedora 5, too.

Although I've a Toshiba with the same IGP, the Radeon XPress 200M.

Can anyone confirm or deny the fix in the previous post? I don't want to hose my WinBlows insta--
;)

Nevermind, I've a spare 40gig layin' around, I'll give it another shot.

---

### Post by sublime on 2006-05-15
you arent going to hose the windows partition.  it doestn do anything with windows this is all with fedora.  and its not a fix its just installing the ati drivers.

---

### Post by zerofx on 2006-05-16
[quote=sublime]you arent going to hose the windows partition.  it doestn do anything with windows this is all with fedora.  and its not a fix its just installing the ati drivers.[/quote] 
I mean't as in wipin' the drive in installin' Ubuntu or Fedora, because I attempted both with less than flattering results, as in, unable to 'startx' because of the hardware installed in this laptop.

;)

But if you're sayin' I can do this from the commandline, which I think you already pointed out, I can make it happen.

:cool:

---

### Post by Israfel on 2006-05-19
Awesome, I thought I was the only one with this problem. Do any of you know if anything needs to be changed in order to do this with Kubuntu?

---

### Post by zerofx on 2006-05-20
So far I'm unable to do anything but be in total-commandline-mode.
Can't 'sudo' anything, can't even install the ATi driver, as the installer for (K)Ubuntu doesn't prompt me for an admin password, only a password for the user.

---

### Post by Egad on 2006-05-20
[QUOTE=pr0phet1024]Exactly the same problem here! has anyone found a fix for this?[/QUOTE]

yes. I have.

I just spent the past 2 days (entire days) getting the graphics fully working.

I'm using an hp pavilion dv5000 laptop (dv5020us to be exact) and am using the K7 architecture 'build' in the 32-bit version of Ubuntu 5.1 from the DVD install

I should point out im very green when it comes to linux..  it was definately a learning process... so I'm going to assume newbie status here and go from there..  nothing specific to anyone.. 

ok so heres what I did.


I first did this:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI) go here and print this guide out

then fast forward to where it says "Using the drivers from ati.com"

I went ahead of time and downloaded the ati linux drivers to my memorystick through windows (im dual booting)

then i made a temp directory (mkdir temp) in my ~ home dir and moved them there (getting ubuntu to sense my memory stick was a thing in itself whew)

but anyways then I just did the commands in step 3 (note im in command line mode - I defaulted back there o/c b/c X doesnt load)

then do the commands starting with sudo dpkg -i *.deb etc etc etc

reboot where it says to .. might/should still have problems loading X 

ok so then I went to /etc/X11 and edited xorg.conf in vi (vi /etc/X11/xorg.conf) go to where it has the device and change it from "ati" to "fglrx"

make sure you have write access to the xorg.conf file (chmod 777 xorg.conf - security issue? i didnt care personally)
 
then I went to /etc/X11/Xsession.d/ and removed the 10fglrx file (theres further info about this in the driver installation guide you printed out)

rebooted

not only do I have 2d but now I have 3d working too :)

btw if you just want ANY gui just edit the xorg.conf where it says ati change it to say vesa save and reboot you'll get slow 2d but at least you'll get something.

best of luck

btw heres my xorg.conf for reference.. I may have done other tweaking.. again it took me 2 very long days getting this 100%

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "pc104"
        Option          "XkbOptions"    "pc104"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "fglrx"
        BusID           "PCI:1:5:0"
#       Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection

```

---

### Post by zerofx on 2006-05-21
Coolios, linux itself, in my mind, is all aboot DIY and tweaking to your liking.
I'll have to attempt this one more time, I'm swappin' harddrives in my laptop everytime I try linux.

---

### Post by macdo on 2006-05-21
[quote=zerofx] 	So far I'm unable to do anything but be in total-commandline-mode.
Can't 'sudo' anything, can't even install the ATi driver, as the installer for (K)Ubuntu doesn't prompt me for an admin password, only a password for the user.[/quote]

Ubuntu doesn't have a root password. To sudo, you use your user password.
(That's one of the major Ubuntu differences, BTW)

---

### Post by zerofx on 2006-05-21
I did, and all I got was an unable to authenticate error.
Hmmmmm.

---

### Post by macdo on 2006-05-21
That's just plain weird. 

Have you tried a Dapper live CD?

---

### Post by zerofx on 2006-05-22
[QUOTE=macdo]That's just plain weird. Have you tried a Dapper live CD?[/QUOTE] Actually, once I managed to edit the xorg.conf with VIM I was all set and I got limited 2D without acceleration, but I can't install the ATI drivers with the aformentioned instructions, because all I get is an "unsupported architecture" error when I do: ```
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy
``` I'm in Kubuntu breezy, btw, should that make a difference?

---

### Post by sublime on 2006-05-22
are you trying this on ppc or 64-bit?  in which case go here: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and find your architecture from there.

---

### Post by zerofx on 2006-05-22
[quote=sublime]are you trying this on ppc or 64-bit?  in which case go here: [http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page") and find your architecture from there.[/quote]

No, it's the standard 32-bit i386 version.

---

### Post by zerofx on 2006-05-28
Also, I can't generate distro-specific packages, it keeps erroring and tellin' me that Ubuntu/breezy is unsupported.

---

### Post by leju on 2006-06-03
I also had this problem with Breezy. I just upgraded to the new Dapper 6.06. Using the Live install worked with no problems, and the ATI Xpress 200 was detected using the 'ATI' module. I later tried the FGLRX ATI module but there are shutdown/Restart crash issues with it on this card, so stick to the 'ATI' module.

Dapper also seems much more responsive in terms of GNOME. I recommend it for anyone with the Xpress 200 chip.

Hope this helps.

---

### Post by lukemh on 2006-06-07
[QUOTE=sublime]im using the same card on my compaq.  in command more run:

```


sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #select the "vesa" module

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run
(this will download the ati driver from the ati website)

sudo apt-get install gcc-3.4 module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
cd directory of ati driver
chmod +x ati-driver-installer-8.24.8-x86.run
LANG=C LC_ALL=C ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/breezy
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb

sudo rm /usr/src/fglrx-kernel*.deb

sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant a-i fglrx

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

reboot

```

this was taken from the walk through on [http://wiki.cchtml.com](http://wiki.cchtml.com)[/QUOTE]



i am using dapper, and had a working gui but i played with xconf and couldnt get gui back even when i restored the conf file witht he backup i made..

soo..

i followed these commands above and i have my gui back... i even have the widescreen 1280x768 i wanted which is why i was playing with my xconf in the first place... when i came back into ubuntu with gui i was propted to update my ati driver ... i did! 

all is well!!! thanks

from... a newbie. lukemh

---

