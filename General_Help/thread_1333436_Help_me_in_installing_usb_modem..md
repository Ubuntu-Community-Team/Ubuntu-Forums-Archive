---
title: "Help me in installing usb modem."
date: 2009-11-21
forum: General Help
---

### Post by anikondemand on 2009-11-21
Help me in installing usb cdma dialup modem.

Got the complete steps to install from some other thread here itself, but facing problems:blush:.

These are the steps which I found in that thread.

> Step 1: (To ensure that the usb modem is detected by the kernel)

Connect the usb modem and type

sudo tail -f /var/log/messages

Check if the following messages are displayed

Oct 29 17:08:52 birenjith-laptop kernel: [18094.628000] usb 3-1: new full speed USB device using uhci_hcd and address 7

Oct 29 17:08:52 birenjith-laptop kernel: [18094.784000] usb 3-1: configuration #1 chosen from 1 choice

Oct 29 17:08:52 birenjith-laptop kernel: [18094.792000] usbserial_generic 3-1:1.0: generic converter detected

Oct 29 17:08:52 birenjith-laptop kernel: [18094.792000] usb 3-1: generic converter now attached to ttyUSB0


If the message is displayed, your usbmodem is getting detected automatically. Most likely it wont happen - only the first two lines will be displayed. Then, do the following. 

Step 1.1 (In case of ubuntu linux installation, need changes in /etc/init.d/mountdevusbfs.sh)


Go to /etc/init.d/mountdevusbfs.sh and check if the following lines are commented in the do_start() function



#

# Magic to make /proc/bus/usb work

#

mkdir -p /dev/bus/usb/.usbfs

domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644

ln -s .usbfs/devices /dev/bus/usb/devices

mount --rbind /dev/bus/usb /proc/bus/usb



If they are commented, uncomment them.

Step 1.2 (To attach the usbserial module to the kernel) 

First, we need to find out the vendor id and product id of the usb modem. Type lsusb or lsusb -v to identify the vendor & product id of the usb modem. For the usb modem which shows up as CBP VIA Telecom in Windows, the vendor id is 0x15eb and product id is 0x0001.

Now attach the module usbserial to the kernel by typing the command

sudo modprobe usbserial vendor=0x1d6b product=0x0001

To make it happen everytime the system boots, add the following line to the file /etc/modules
usbserial vendor=0x15eb product=0x0001

After these steps, the usb device would have been detected. 

Step 2: (To edit wvdial configuration file)

Back up the /etc/wvdial.conf and then edit the /etc/wvdial.conf to add the following lines

[Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0

Modem Type = Analog Modem

ISDN = 0

Phone = #777

Modem = /dev/ttyUSB0

Username = <username>
Password = <password>
Baud = 460800

Stupid Mode = 1

Auto DNS

Check Def Route


Step 3: (Connect)

Type wvdial to connect to internet

Done step 1. After the command lsusb in the step 1.2, I'm getting the following output.

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 1c4f:0003  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID **15eb:0001**  
Bus 002 Device 002: ID 413c:8000 Dell Computer Corp. BC02 Bluetooth USB Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The highlighted one seems to be my usb modem. I have only 2 usb ports. One is used by modem and the other one by usb mouse.

Is it detected as per the above output?

And on giving the command sudo modprobe usbserial vendor=0x1d6b product=0x0001, it says device not found or something like that:(.

Help:blush:.

Step 2: (To edit wvdial configuration file.) : I didnt find /etc/wvdial.conf file. So I created one and added the following.
> [Dialer Defaults]

Init1 = ATZ

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Init3 = at+crm=1;+cmux=1;+cps=33;+cta=0

Modem Type = Analog Modem

ISDN = 0

Phone = #777

Modem = /dev/ttyUSB0

Username = <username>
Password = <password>
Baud = 460800

Stupid Mode = 1

Auto DNS

Check Def Route

And as per step 3, while trying to connect, it gives :
> abc@ubuntu:~$ wvdial
The program 'wvdial' is currently not installed.  You can install it by typing:
sudo apt-get install wvdial
bash: wvdial: command not found


abc@ubuntu:~$ sudo apt-get install wvdial gives :
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wvdial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wvdial has no installation candidate


:confuse:

This is my /etc/modules file :
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
usbserial vendor=#

# Magic to make /proc/bus/usb worki

#

mkdir -p /dev/bus/usb/.usbfs

domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644

ln -s .usbfs/devices /dev/bus/usb/devices

mount --rbind /dev/bus/usb /proc/bus/usb
 product=0x0001


Help.

---

### Post by AlphaLexman on 2009-11-21
What version of ubuntu are you using?

I have a usb broadband modem on 9.04 and I connect with NetworkManager instead of wvdial. However on my wife's 7.10 machine I had to go with the wvdial option. I did make sure the modem was plugged in during install on my machine, so the kernel problems you're having didn't affect me.

---

### Post by anikondemand on 2009-11-21
I'm using ubuntu 9.04 Desktop Edition.
But bro, mine is not a broadband connection. Its dialup. Modem is detected as Via Telecom CBP USB modem in Windows. Didnt find any linux driver for the same.

Followed the instruction in some other thread as above, but I'm facing difficulties as mentioned above.

---

### Post by AlphaLexman on 2009-11-21
Try this:

If NetworkManager isn't running, 

```
sudo NetworkManager
```

Right-click the NetworkManager icon on the taskbar, Edit Connections, and see if your modem is found. [probably a tab at the top] Click 'Add' and on my machine a little wizard will help you setup a new connection.

If you think that wvdial is the way to go, 

```
apt-cache search wvdial
```
> libwvstreams4.4-extras - C++ network libraries for rapid application development
wvdial - PPP dialer with built-in intelligence
gnome-ppp - modem internet connection tool for the GNOME Desktop

```
sudo apt-get install gnome-ppp
sudo apt-get install wvdial
```

---

### Post by anikondemand on 2009-11-22
I will try it and post my results here.

---

### Post by anikondemand on 2009-11-22
Replaced ubuntu 9.04 with version 8.04

Now only one problem left. Modem is detected and I am able to dial. Once it has shown "Data call in progress" on my modem.
But after that, it gives an error in Terminal that password is incorrect.

I gave the same usn/pwd which I use in Windows.

Help.

---

### Post by anikondemand on 2009-11-22
Facing problem with wvdial.

Output of wvdial :
> --> Ignoring malformed input line: "Auto DNS"
--> Ignoring malformed input line: "Check Def Route"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: at+crm=1;+cmux=1;+cps=33;+cta=0
at+crm=1;+cmux=1;+cps=33;+cta=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
~[7f]}#@!}!}!} }-}#}%B#}%}'}"}(}"{B~
--> Carrier detected. Starting PPP immediately.
--> Starting pppd at Sun Nov 22 14:14:07 2009
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6746
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08][10]&#65533;[06][08]
--> Disconnecting at Sun Nov 22 14:14:10 2009
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)

Help.

---

