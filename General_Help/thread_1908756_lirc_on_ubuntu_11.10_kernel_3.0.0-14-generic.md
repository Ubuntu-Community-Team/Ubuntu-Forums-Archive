---
title: "lirc on ubuntu 11.10 kernel 3.0.0-14-generic"
date: 2012-01-14
forum: General Help
---

### Post by frostyboy33 on 2012-01-14
Hi all,

First time poster so please be nice :p i will try and provide as much relevent information as i can

info:
REMOTE: logitech harmony 600 - setup for a gaming console with DVD (this si what all the guides have said)
IR-RECIEVER: Media Center Ed. eHome Infrared Remote Transceiver (0609:031d)
UBUNTU: 11.10
KERNEL: 3.0.0-14-generic

Please find below out put of a number of commands i have used to verify that the ir-reciever is being picked up etc

lsusb
```
Bus 005 Device 002: ID 0609:031d SMK Manufacturing, Inc. eHome Infrared Receiver
```cat /proc/bus/input/devices
```
I: Bus=0003 Vendor=0609 Product=031d Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (0609:031d)"
P: Phys=usb-0000:00:1d.0-2
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4
B: PROP=0
B: EV=100013
B: KEY=fff 0 200108fc32e 237605100000000 0 700158000 419200000001 9e968000000000 10000000
B: MSC=10
```so from this i am fairly sure that the IR-reciever is being picked up by the system

when i run either irw or ir-keytable -t i get no response what so ever.
i have tried to get the raw output from the device as well i am not 100% sure if i am doing that correctly though so if someone could show me how that would be great

i have followed a number of different posts to try and make my remote work

[http://ubuntuforums.org/showthread.php?t=1845564](http://ubuntuforums.org/showthread.php?t=1845564)
[http://www.gossamer-threads.com/lists/mythtv/users/499528](http://www.gossamer-threads.com/lists/mythtv/users/499528)

but unfortunately none of them have worked especially as everything seems to be either out of date or not for lirc0.9.0 or my version of ubuntu

my /etc/lirc/lircd.conf and /etc/lirc/hardware.confare as default as they get

i have run dpkg-reconfigure lirc to generate the correct config files.

when i press buttons on my remote the IR-reciever light comes on but i just see no output.

i also know that there have been a lot of changes to mceusb and lirc0.90 so why i keep going around in circles i think it would be great if a new update guide was created(and if there is one i would love to know where it is)

any help would be much appreciated.

thanks in advance

frosty

---

### Post by frostyboy33 on 2012-01-14
Hi there,

i really hope someone might have an idea on this

frosty

---

### Post by kenmy on 2012-01-15
My configuration is very similar to yours and I too have this problem.
My workaround: after finished system boot manually restart lirc:
```

sudo service lirc restart

```
After running this command irw is works normally ro restart system. But in my case xbmc not works before it restart.
My assumption: order start deamons or kernel modules not correct. And one deamon/module not initialising at starting dependent. But I don't understand what lirc must work inside and what order must be at load modules/deamons.
I want to understand how to determine what prevents run the lirc at startup. And fix it.
And I ask the community for help in locating the problem.

Thank you.

---

### Post by frostyboy33 on 2012-01-16
Hi

Kenmy unfortunately that does not solve my problem i have tried multiple times stopping starting and restarting lircd to try and get it to work.

on a  side note though Kenmy you should be able to add a line in /etc/rc.local in order to restart your lircd and that way it will be the last thing executed

again if anyone else has any ideas about my problem i am all ears

Frosty

---

### Post by kenmy on 2012-01-16
Hi,
i found solution 
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

```Important line:
LOAD_MODULES="false"
Antduplicate key press for X applications (Ex: XBMC):
```

Section "InputClass"
   Identifier "Ignore MCE Remote" # any name
   MatchProduct "Media Center Ed. eHome Infrared Remote Transceiver (0471:0815)"
   MatchIsKeyboard "true"
   Option "Ignore" "true"
Endsection

```Replace MatchProduct on your receiver and paste into xorg.conf.
And I turn off inputlirc, in my case licr normally work without inputlirc
```

#update-rc.d inputlirc disable

```May be I changed anything else.

Best regards, KEN.

---

### Post by lerrup on 2012-01-18
> **frostyboy33 said:**
> Hi

Kenmy unfortunately that does not solve my problem i have tried multiple times stopping starting and restarting lircd to try and get it to work.

on a  side note though Kenmy you should be able to add a line in /etc/rc.local in order to restart your lircd and that way it will be the last thing executed

again if anyone else has any ideas about my problem i am all ears

Frosty

Unfortunately I don't as I am in a similar position - everything worked until I upgraded to 11.10 and now my MCE receiver is not activated at all (but is detected).

So any ideas on trouble shooting from anyone would be great.

---

### Post by Kissell on 2012-03-12
did you ever get this fixed?

I have the same problem.

I have tried multiple IR receivers and multiple IR remotes, and can't get "irw" to work with any of them.  Yet, the IR receivers get power and recognize button clicks, and the OS detects the USB devices (they show up in /dev/input/by-id)

---

