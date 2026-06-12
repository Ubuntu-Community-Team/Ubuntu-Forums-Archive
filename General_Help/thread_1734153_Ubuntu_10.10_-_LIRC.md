---
title: "Ubuntu 10.10 - LIRC"
date: 2011-04-19
forum: General Help
---

### Post by irishetalon007 on 2011-04-19
Hello,

I'm really hoping someone can help me. I want to pull my hair out! I've been working on this a couple hours a week for the past few months. No I'm not exaggerating.

I have a windows MCE remote and USB receiver.

the remote/receiver model number is a rosewill RRC-127. Others who have bought this remote say it works with ubuntu 10.10 LIRC "out of the box." I've tried clean installs of Ubuntu, completely wiping the hard drive, and every time I STILL can't get it to work "out of the box." 

There was ONE point in time where I got something to show up in irw! so i at least know that the device works. But then I tried cleaning up installs that I thought might have been extraneous like python-lirc, kremote, x-lirc, etc., and it stopped working at some point in the process.

This most recent time, my procedure was as follows:

-Clean install of Ubuntu 10.10. Including wiping the drive first.
-Installed LIRC and gnome-lirc-properties.
-during LIRC install, it asks for your receiver -  I selected "Windows MCE (all)"
-Restarted.
-tried irw - nothing.
-then i tried configuring gnome-lirc-properties, and it wouldn't start. I looked up why not and found that I have to install hal, so I did, then gnome-lirc-properties started, and I configured it using the auto-detect button.
-after restarting, irw still shows nothing

I'm at a loss.

here is my /etc/lirc/hardware.conf

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_mceusb"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD=true

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="TSGH-IR01"
REMOTE_VENDOR="HP"

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Topseed\ eHome\ Infrared\ Transceiver\ \(0x0011\)"
RECEIVER_VENDOR="TopSeed\ Technology"




any help is GREATLY appreciated.

---

### Post by ghostborg on 2011-04-20
I have a Windows MCE remote and usb dongle which after I install Lirc just like you did does nothing unless a program like XBMC uses it. For me it does work with XBMC out of the box. When I exit XBMC it does not do anything from the desktop.

In a terminal I enter:
```
lsusb
```
which displays TopSeed Technology Corp. eHome Infrared Transceiver

My usb dongle model is a GP-IR02BK .

---

### Post by tylersontag on 2011-06-09
did you ever have any luck getting this to work?

---

### Post by davewithhemp on 2011-06-10
I just started another thread on this same subject. We need a fix for this.
 
[http://ubuntuforums.org/showthread.php?p=10925413#post10925413](http://ubuntuforums.org/showthread.php?p=10925413#post10925413)

---

### Post by irishetalon007 on 2012-02-05
Follow above links for fix

THANKS!!!

---

