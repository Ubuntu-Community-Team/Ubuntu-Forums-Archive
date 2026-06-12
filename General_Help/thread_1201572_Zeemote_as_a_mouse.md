---
title: "Zeemote as a mouse ?"
date: 2009-07-01
forum: General Help
---

### Post by nigelmouse on 2009-07-01
I've just received a [Zeemote]("http://www.zeetoo.net/website/support_js1.html") and figured I'd be able to use it as a bluetooth mouse. 

I've got 9.04 installed and I can pair against the Zeemote using the Gnome bluetooth applet. The Zeemote shows up in the list with a mouse icon next to it so I figure it is appearing as a bluetooth mouse. While the pairing is successful the device does not connect. Clicking the plug icon (the connect button I presume) in the bluetooth prefrences dialog just makes the icon grey out, the the Zeemote stays in pairing mode.

The output of hcitool info is as follows:

```
sudo hcitool info 00:1C:4D:01:0C:5C
Requesting information ...
	BD Address:  00:1C:4D:01:0C:5C
	Device Name: Zeemote JS1
	LMP Version: 2.0 (0x3) LMP Subversion: 0x10b7
	Manufacturer: Cambridge Silicon Radio (10)
	Features: 0xff 0xff 0x8f 0xf8 0x1b 0x18 0x00 0x80
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
		<HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
		<power control> <transparent SCO> <broadcast encrypt> 
		<enhanced iscan> <interlaced iscan> <interlaced pscan> 
		<inquiry with RSSI> <extended SCO> <EV4 packets> <EV5 packets> 
		<AFH cap. slave> <AFH class. slave> <AFH cap. master> 
		<AFH class. master> <extended features>
```

Does anyone know if this device can be used as a bluetooth mouse, and if so what I'm doing wrong ?

---

### Post by danmiddle2 on 2009-11-14
try this, it might work;

sudo apt-get install libbluetooth-dev
wget [http://www.harbaum.org/till/maemo/zeemoted.tgz](http://www.harbaum.org/till/maemo/zeemoted.tgz)
tar xvzf zeemoted.tgz 
cd zeemoted-1.0/
make
sudo make install
sudo modprobe uinput
zeemoted

at this point you should have your zeemote working as a bluetooth joystick on linux (thats all i've done).

then to get it working as a mouse:

sudo aptitude install joystick xserver-xorg-input-joystick
sudo nano /etc/X11/xorg.conf

add this bit, modify the jsX number

Section "InputDevice"
	Identifier	"Joystick"
	Driver	"joystick"
	Option "Device" "/dev/input/js0"
	Option "SendCoreEvents" "true"
EndSection

add this within server layout

	Inputdevice	"Joystick"

Good luck!

---

### Post by hitman72 on 2011-04-21
I bought this Zeemote JS1. since I'm a newbie to ubuntu, I do not know how to change this guide to ubuntu 10.10. I installed the driver, "zeemoted" from shell detects the motions and the key pressure of JS1 but I do not know how change the part of "xorg.conf" from ubuntu 9.04 to ubuntu 10.10. In ubuntu 10 I have seen that the xorg.conf has become a folder and is in "/ usr/share/X11/xorg.conf.d". can anyone help me? thanks

---

### Post by hitman72 on 2011-05-02
hi, following some guides on how to use Bluetooth devices with ubuntu 10.10 or higher I created a file named "20-zeemote.conf" (say the name for it is irrelevant (?)) inside "usr/lib/X11/xorg.conf.d "
 and inside there I copied:

Section "InputDevice"
Identifier "Joystick"
Driver "joystick"
Option "Device" "/dev/input/js0"
Option "SendCoreEvents" "true"
EndSection

changing only the "line"
Section "InputDevice" **[COLOR=Black]in[/COLOR]** Section "InputClass"

on restart of ubuntu unfortunately the mouse icon disappears (both the physical and the touchpad mouse does not work), it works just the keyboard. With a livecd deleting the file "20-zeemote.conf" everything back to normal. repeat (sorry) for an expert in ubuntu should be an easy change. ciao :-)

---

### Post by hitman72 on 2011-05-05
Hi, reading a bit 'around on the joypad and mouse issues in general, finally to use zeemoted like a mouse I had to delete/backup the file "50-joystick.conf" in directory "/usr/share/X11/xorg.conf.d/" (conflict?) and then I have created a file "called 50-zeemote.conf" using this:

Section "InputClass"
    Identifier "Joystick"
    MatchDevicePath "/dev/input/js0"
    Driver "joystick"
    Option "SendCoreEvents" "1"
EndSection

Now when I start Ubuntu 10.10 from shell I launch
"sudo zeemoted" and the mouse pointer is "driven" by zeemote. The
problem is that the mouse movement is very very very random and shaky.
Going UP or LEFT is quite accurate but going DOWN or RIGHT is very
terrible! shaky and random. Without creating the file "50-zeemote.conf" and instead using QjoyPad, things are looking a little better, but everything remains unusable. it's kind of "dead zone" or calibration problem... Whereas driver is made &#8203;&#8203;to use the zeemote as a joypad maybe we can not get better use... thank you and sorry for my poor english. ciao :-)

---

### Post by lpt2007 on 2011-05-29
> **hitman72 said:**
> Hi, reading a bit 'around on the joypad and mouse issues in general, finally to use zeemoted like a mouse I had to delete/backup the file "50-joystick.conf" in directory "/usr/share/X11/xorg.conf.d/" (conflict?) and then I have created a file "called 50-zeemote.conf" using this:

Section "InputClass"
    Identifier "Joystick"
    MatchDevicePath "/dev/input/js0"
    Driver "joystick"
    Option "SendCoreEvents" "1"
EndSection

Now when I start Ubuntu 10.10 from shell I launch
"sudo zeemoted" and the mouse pointer is "driven" by zeemote. The
problem is that the mouse movement is very very very random and shaky.
Going UP or LEFT is quite accurate but going DOWN or RIGHT is very
terrible! shaky and random. Without creating the file "50-zeemote.conf" and instead using QjoyPad, things are looking a little better, but everything remains unusable. it's kind of "dead zone" or calibration problem... Whereas driver is made &#8203;&#8203;to use the zeemote as a joypad maybe we can not get better use... thank you and sorry for my poor english. ciao :-)

I followed this instructions but Zeemoote JS1 not working as a mouse in Ubuntu 11.4. 

Can someone help me out? :confused:

---

