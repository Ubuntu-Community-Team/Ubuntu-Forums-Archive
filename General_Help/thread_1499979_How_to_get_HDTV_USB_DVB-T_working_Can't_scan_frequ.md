---
title: "How to get HDTV USB DVB-T working? Can't scan frequencies.  dvb-usb-af9015 (afatech)"
date: 2010-06-02
forum: General Help
---

### Post by Svens on 2010-06-02
Hello everybody and have a nice day!
I have got a little problem here with my new HDTV USB DVB-T receiver.
My USB stick is this one:
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=370307620849&ssPageName=STRK:MEWNX:IT](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=370307620849&ssPageName=STRK:MEWNX:IT)
I can't get it to scan my frequencies.
PC finds the stick (lsusb):
```
Bus 002 Device 005: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick

```
When I plug it in, dmesg shows this:
```
[ 5680.696043] usb 2-2: new high speed USB device using ehci_hcd and address 7
[ 5680.834917] usb 2-2: configuration #1 chosen from 1 choice
[ 5680.849872] af9015: tuner id:179 not supported, please report!
[ 5680.852951] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
[ 5680.853438] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1/input/input14
[ 5680.853644] generic-usb 0003:15A4:9016.0005: input,hidraw1: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-2/input1

```
I installed from Synaptic package "dvb-apps" and "linux-firmware-nonfree".
As I read on the internet, if everything is fine, then when I plug the USB in, it should create directory /dev/dvb/, but it does not. Then I found on the internet a script file named "MAKEDEV-DVB.sh", which creates the necesary directory, because if the directory is not created, then after ```
sudo scan /usr/share/dvb/dvb-t/lv-Riga

```
it shows
```
scanning /usr/share/dvb/dvb-t/lv-Riga
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```
But if the directory is created, then after the same command I have
```
scanning /usr/share/dvb/dvb-t/lv-Riga
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

```
I found on the internet a firmware for my USB HDTV DVB-T stick named "dvb-usb-af9015.fw" and copied it into /lib/firmware/ but I have not seen any difference with that.

That is as far as I can get. I don't know what to do next. Could anyone please help me with this? Any help is appreciate. 
Thank you!

---

### Post by inameiname on 2010-06-02
Alright, well sounds like you have the firmware, and in the right place. Next thing required is to ensure you have dvb-apps and v4l-dvb installed as well. Those three things are required. And sounds like you have dvb-apps already, at least the older version that's in the repos.

[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

[http://linuxtv.org/hg/dvb-apps/archive/tip.tar.bz2](http://linuxtv.org/hg/dvb-apps/archive/tip.tar.bz2)

However, I noticed with Lucid, you have to do one more thing when installing the v4l-dvb tar file:
In the 'v4l' folder, open the .config file in the 'v4l' subfolder  (created only after you 'make' it first), and find the line:  CONFIG_DVB_FIREDTV=m and change it to CONFIG_DVB_FIREDTV=n, and then  'make' (again) and 'sudo make install'. (FYI, this all takes several  minutes.) Then reboot.

Finally, after all that, here is what I use to scan for channels:

- I like SMPlayer, but VLC and many others work too

    To record digital channels:

        mencoder dvb://"whatever the channel is" -o whatever.avi -oac copy -ovc copy
        mencoder dvb://"whatever the channel is" -o whatever.avi -oac mp3lame -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1500:vhq

- To scan for digital channels:

    sudo scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > ~/Temp/channels.conf.atsc
    sudo scan /usr/share/dvb/atsc/us-NTSC-center-frequencies-8VSB > ~/Temp/channels.conf.ntsc
    sudo scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/Temp/channels.conf.cable_standard
    sudo scan /usr/share/dvb/atsc/us-Cable-IRC-center-frequencies-QAM256 > ~/Temp/channels.conf.cable_irc
    sudo scan /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256 > ~/Temp/channels.conf.cable_hrc
    sudo scan /usr/share/dvb/atsc/us-Cable-EIA-542-HRC-center-frequencies-QAM256 > ~/Temp/channels.conf.cable_eia_542_hrc
    sudo scan /usr/share/dvb/atsc/us-Cable-EIA-542-IRC-center_frequencies-QAM256 > ~/Temp/channels.conf.cable_eia_542_irc

...and when done with whatever scan works for you (the first is probably the one you want), remove the last part of the file name (the .atsc, .ntsc, etc), and put the channels.conf into whatever application folder you are using to watch (.mplayer is what you must put it into for SMPLayer).

---

### Post by Svens on 2010-06-02
Hi, Inameiname!
Thank you very much for your high-level reply!
I did everything as you said (even installed dvb-apps which you gave). Everything, I think, was going smooth, but somehow the scanning does not want to happen. When I try to execute the scan commands you gave me, I'm having error because the ~/Temp/channels.conf.atsc file does not exist. But I saw that I have a channels.conf file in my home directory, so I used it, but the error I have after that is unfortunately the same:
```
svens@svens-hp:~$ sudo scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > ~/channels.conf
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
svens@svens-hp:~$ 

```
If I make the needed directory myself with the script "MAKEDEV-DVB.sh", then the error is like this again:
```
 svens@svens-hp:~$ sudo scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > ~/channels.conf
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device
svens@svens-hp:~$ 
```
Does that means that I did something wrong with what you told me?
Thank you for your patience!

---

### Post by inameiname on 2010-06-03
If you were able to install everything just fine, it seems you are doing just fine. Sounds like it's just the scan function that's screwy for some reason.

Here is my suggestion:

Perhaps write out whatever directory you want at the end, such as:

sudo scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB > /home/(your username)/(wherever you want)

I've noticed sometimes the '~/' command doesn't work. That and/or because you don't already have a '/Temp' folder, which I already do, it errors because as it says to you, it doesn't exist.

Oh, and I doubt I have to mention you must have your usb adapter plugged in prior to scan. 

Another scanning method which is similar but allow for more options is w_scan, as seen here:

[http://edafe.org/vdr/w_scan/](http://edafe.org/vdr/w_scan/)

...and I think you can install it as well through the repos:

sudo apt-get install w-scan

Just another option if the other doesn't seem to be working for you.

One final thing to suggest, try the scan procedure without 'sudo' and see what happens. I just thought of having a very similar problem when I first got mine to work and after several attempts it suddenly worked, and thinking about it, it may be because of the lack of 'sudo'. Worth a shot.

---

### Post by wirbel2 on 2010-06-03
If you're looking for w_scan, the main page isn't edafe.org, but [http://wirbel.htpc-forum.de/w_scan/index_en.html](http://wirbel.htpc-forum.de/w_scan/index_en.html)


However, here seem to be several things to be mixed up. DVB-T is _different_ from north-american ATSC/VSB. And DVB-T means usually *not* HDTV, but digital SDTV.

Next thing which is wrong, is the usage of MAKEDEV-DVB.sh.
You should not use this script, since every new distribution uses udev to create /dev/dvb/*.
If those files are missing on your system, it means that the dvb driver is not loaded for your device. As soon as the driver is successfully loaded, udev will create automatically /dev/dvb/* for you.
Before doing anything else, please reboot your machine or delete manually /deb/dvb/*.

Please go to [www.linuxtv.org](www.linuxtv.org) and try to collect information about the drivers needed for your special DVB-T device. Try to load the correct driver and enshure afterwards that loading suceeds using the 'dmesg' command.

If you find in the dmesg output something like 'registering frontend0' you have successfully loaded the driver and only after that you may continue.

us-atsc tuning data for scan are for North-Americans only.

---

### Post by Svens on 2010-06-03
Thank you for your answers! They are helping me a lot!
But I have a problem with loading the needed drivers. I am reading this guide: [http://linuxtv.org/hg/v4l-dvb/file/304cfde05b3f/linux/Documentation/dvb/README.dvb-usb](http://linuxtv.org/hg/v4l-dvb/file/304cfde05b3f/linux/Documentation/dvb/README.dvb-usb) 
and as I understand, I have to load the needed driver manualy, and to do so, I have to do this:
>  135 1.3. Loading the drivers
136
137 Hotplug is able to load the driver, when it is needed (because you plugged
138 in the device).
139
140 If you want to enable debug output, you have to load the driver manually and
141 from withing the dvb-kernel cvs repository.
142
143 first have a look, which debug level are available:
144
145 modinfo dvb-usb
146 modinfo dvb-usb-vp7045
147 etc.
148
149 modprobe dvb-usb debug=<level>
150 modprobe dvb-usb-vp7045 debug=<level>
151 etc.
152
153 should do the trick.
154
155 When the driver is loaded successfully, the firmware file was in
156 the right place and the device is connected, the "Power"-LED should be
157 turned on. 

I just don't understand, what I have to do. If I write in terminal "modinfo dvb-usb", then I get this:
```
svens@svens-hp:/lib/modules/2.6.32-21-generic/build$ modinfo dvb-usb
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb.ko
license:        GPL
description:    A library module containing commonly used USB and DVB function USB DVB devices
author:         Patrick Boettcher <patrick.boettcher@desy.de>
version:        1.0
srcversion:     E7193EAB9E744E9E3CA66A1
depends:        dvb-core
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           debug:set debugging level (1=info,xfer=2,pll=4,ts=8,err=16,rc=32,fw=64,mem=128,uxfer=256  (or-able)). (debugging is not enabled) (int)
parm:           disable_rc_polling:disable remote control polling (default: 0). (int)
parm:           force_pid_filter_usage:force all dvb-usb-devices to use a PID filter, if any (default: 0). (int)
svens@svens-hp:/lib/modules/2.6.32-21-generic/build$ 

```
If I write "modinfo dvb-usb-vp7045", then I get this:
```
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/media/dvb/dvb-usb/dvb-usb-vp7045.ko
license:        GPL
version:        1.0
description:    Driver for Twinhan MagicBox/Alpha and DNTV tinyUSB2 DVB-T USB2.0
author:         Patrick Boettcher <patrick.boettcher@desy.de>
srcversion:     2D57FDE91FBC3D069400268
alias:          usb:v13D3p3224d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3223d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3206d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3205d*dc*dsc*dp*ic*isc*ip*
depends:        dvb-usb
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           debug:set debugging level (1=info,xfer=2,rc=4 (or-able)). (debugging is not enabled) (int)
parm:           adapter_nr:DVB adapter numbers (array of short)
svens@svens-hp:/lib/modules/2.6.32-21-generic/build$ 

```

And I don't understand what I am supposed to do with that "debuging" and "have a look, which debug level are available". What I am supposed to do with that info?

I am sorry for my lack of knowledge. I hope that someone could explain that to me. Thank you!

---

### Post by wirbel2 on 2010-06-03
Well, in most cases you dont need to enable extra debug infos at all. In the rare cases where you have to dig into a problem, only in that case you may need this.

Loading some kernel module means

open an xterm window and type 'modprobe >MODULE_NAME>' with <MODUL_NAME> to be replaced by the name of the actual module. If you need to pass parameters to an kernel module, just add it to the command, for example

modprobe dvb-usb-vp7045 debug=7

note: 7 = bitwise or of : 1 (info) + 2 (xfer) + 4 (rc)


Assuming that your device as an vp7045 dvb usb device (i didnt check..), just type 'modprobe dvb-usb-vp7045' and check afterwards by typing 'dmesg | grep dvb' for success.

---

### Post by piginabox on 2010-07-15
The problem lies in the usbhib driver claiming the device before it can be seen as a DVB device.
In you dmesg..
[ 5680.853644] generic-usb 0003:15A4:9016.0005: input,hidraw1: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:1d.7-2/input1
shows that it is being treated as a keyboard device.

I've asked for a solution here [http://ubuntuforums.org/showthread.php?p=9571736#post9571736]("http://ubuntuforums.org/showthread.php?p=9571736#post9571736") but no joy so far.

I'm using Lucid, though.

---

