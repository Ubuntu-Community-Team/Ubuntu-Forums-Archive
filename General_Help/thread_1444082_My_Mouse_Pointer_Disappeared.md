---
title: "My Mouse Pointer Disappeared"
date: 2010-03-31
forum: General Help
---

### Post by goatgonads on 2010-03-31
Been using Karmic for a while now, love it.

Until my mouse pointer disappeared. The only thing that I have done recently was to install a new video card driver the day before. I reinstalled the old driver, and it didn't make a difference.

Any ideas?

---

### Post by sisco311 on 2010-03-31
What Video card do you have?

What's the content of the xorg.conf file?
```
cat /etx/X11/xorg.conf
```

---

### Post by mechro on 2010-03-31
From a Terminal do **gksudo nautilus**. Navigate to **/etc/X11/xorg.conf**. If it exists, rename **xorg.conf** to **xorg.conf.backup **and reboot.

If it solves your mouse problem you may have to reactivate your graphics card driver but you'll need to figure out how to do it without messing up the mouse again.

If you get the mouse working post the contents of xorg.conf.backup here.

---

### Post by goatgonads on 2010-04-02
Thanks for the tips, video card is an ATI 5870, I do see

Here are the contents of the xorg.conf.backup:

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "nvidia"
    Option        "NoLogo" "True"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
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

---

### Post by mechro on 2010-04-02
Is your mouse pointer working?

Your xorg.conf contains both nvidia and ati configurations which is not good; only one should be configured unless there's some weird and wonderful dual-graphics set-ups that I don't know about. Have you changed your graphics card or do you have on-board graphics as well as a separate card?

If your mouse pointer is working you could try reactivating your ati driver from System > Administration > Hardware Drivers.

---

### Post by goatgonads on 2010-04-03
I changed from an Nvidia card to an ATI card about a month ago, and I have onboard video, that I do not use. Removing xorg.conf does restore my mouse after losing it due to video driver installation.

If I try to re-enable the video driver under System > Administration > Hardware Drivers, it tells me that no "proprietary video drivers are in use on this system", and the only option available is "close"

The driver that I was previously attempting to install is one that was just released by ATI, and not the one offered under System > Administration > Hardware Drivers.

I have tried reinstalling my previous driver and the newer version, I lose my mouse both ways.

I did some research, and removed all of the ATI/Nvidia drivers, did a fresh install of the ati driver, and lost my mouse again. The install from that produced the following xorg.conf:

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
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

---

### Post by vzomik on 2010-04-03
rebuild the file xorg.conf, use the command:
"Xorg -configure"
"cp /root/xorg.conf.new /etc/X11/xorg.conf"

---

### Post by quadproc on 2010-04-03
> **goatgonads said:**
> I changed from an Nvidia card to an ATI card about a month ago, and I have onboard video, that I do not use. Removing xorg.conf does restore my mouse after losing it due to video driver installation.
Supplementary note: I am running HD4870x2 with Catalyst 10.3.

Your unused on board video might cause some problems with X windows if you don't specify a BusID for the primary (your new ATI) graphics board.  There was a bug related to this problem and I do not know if it has been fixed, but briefly the X server would find multiple video devices, could not decide which one to use to interact with the operator, and would simply die, leaving the user with only a CLI.  Adding the BusID for the primary board works around this problem.

> If I try to re-enable the video driver under System > Administration > Hardware Drivers, it tells me that no "proprietary video drivers are in use on this system", and the only option available is "close"The Hardware Drivers utility does **not** necessarily correctly report the driver status of your system.  For example, right now I am using ATI's version 10.3 driver and it is in use and working but the utility reports that no proprietary drivers are in use.  I suggest avoiding the Hardware Drivers utility.

> The driver that I was previously attempting to install is one that was just released by ATI, and not the one offered under System > Administration > Hardware Drivers.

I have tried reinstalling my previous driver and the newer version, I lose my mouse both ways.A couple of things to note: your xorg.conf file has two sections which specify a driver (both different).  My experience with redundant entries in that file is that X windows gets confused and does not work properly.  I suggest commenting out the old section, the one with nvidia in it.  You will need root permission to change the file.  It is a good idea to keep a backup copy of the file before you change it; that way, you can fall back to it if necessary.

You can readily install the new ATI driver by downloading it from ATI and then directing the installation yourself, rather than depending on Hardware Drivers.  I suggest that you first uninstall completely the nvidia driver; remnants of it may cause difficulties so in Synaptic find the old driver and mark it for complete removal.  Or use whatever uninstall provisions the nvidia software provided. Once it is gone then you probably want to temporarily change your xorg.conf file to indicate Driver "ati"; this will cause X windows to use the open source driver and this will be OK for completing the installation.  I suggest putting the downloaded driver into its own directory in your /home directory.  Using a terminal, cd into that directory.  Then
```
sudo chmod 777 <the_ati_file_name>
sudo sh <the_ati_file_name> --keep --install
```This will take you through the installation using ATI's install software. Once that is finished then go back to the xorg.conf file and change the driver to "fglrx" if it isn't already that.  Also look to be sure that your xorg.conf was not contaminated by duplicate entries placed there by the ATI software; I had this problem so I commented out all of the duplicate entries.

After a reboot or an X server restart, you will be running the new driver.  You can type glxinfo on the command line to see some of the information about it.  You can run glxgears to see it action.  A fun test is fgl_glxgears.

After your installation is working then you may wish to delete the driver's installation files.  I suggest keeping the directory around because you will probably need to unistall that driver someday (for example, to upgrade it) and there is an uninstall script in that set that you will need.

Best of luck!

quadproc

---

### Post by goatgonads on 2010-04-03
I removed all of the old nvidia drivers and came up with a new xorg.conf, that correctly shows just one device with the fglrx drivers. The bus ID is 1.0.0 by default, not sure if that is correct. I reinstalled the 10.3 catalyst driver and the problem repeated.

When I enter Xorg -configure I get an error message:

-desktop:~$ Xorg -configure

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

and the error message from glxinfo is:

-desktop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15
 

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
-desktop:~$ A

Just to rule out my hardware, I did a quick install on a 60gb ssd, and the fresh install is able to use the driver without problem.

---

### Post by mechro on 2010-04-03
> **goatgonads said:**
> 

and the error message from glxinfo is:



I think that should be **fglrxinfo**

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by goatgonads on 2010-04-04
fglrxinfo gives "segmentation fault". Also synaptic is reporting a broken package, the package is fglrx-amdcccle, when I attempt to reinstall I get the following:

E: /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.660-0ubuntu4_i386.deb: subprocess new pre-installation script returned error exit status 2

---

### Post by mechro on 2010-04-04
A suggestion...

Rename your xorg.conf to xorg.conf.backup again.

Reboot and uninstall your ati and nvidia stuff again. I would use Synaptic and Mark for Complete Removal but you can use the apt-get commands if you want to.

Reboot and try reinstalling the ati driver that worked. Use this howto... [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Good Luck, it may not work as I notice there are a lot of bugs reported for ati drivers.

---

### Post by goatgonads on 2010-04-04
Attempting to follow the directions from the walk through. I get the following error:

Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.660-0ubuntu4_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.660-0ubuntu4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.660-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried every trick that I could find on google, to no avail. including apt-get -f install.

---

### Post by mechro on 2010-04-04
It looks like there is nvidia stuff still in there. I don't know the commands to fully purge your system. Personally, if I still had remnants of packages after Synaptic Complete Removal and rebooting I'd try and delete the stuff manually.

Perhaps you should wait for better advice.

---

### Post by djoxyk on 2010-04-05
I had the same issue with new ATI drivers. Cursor was invisible. What I did to solve it is just navigated to video settings in xfce and disabled 'hardware acceleration for cursor'. It appeared after reboot.

---

### Post by goatgonads on 2010-04-05
Thanks for the replies, I have thrown in the towel, backed up my files, and reinstalled. Trying out the Lucid beta release, seems great so far!

---

### Post by djoxyk on 2010-04-05
> **goatgonads said:**
>  Trying out the Lucid beta release, seems great so far!

watch it :) 
i had this issue on lucid. Make sure you do not accelerate cursor.

---

### Post by goatgonads on 2010-04-05
I went back to the nvidia card temporarily due to the ATI issues that the beta release is having. Considering ebaying the ATI 5870 because ATI historically seems to be not as supportive as Nvidia regarding open source. Wish I would have known that a few months ago.

---

