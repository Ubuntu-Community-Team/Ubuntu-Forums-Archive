---
title: "Remote control daemon not running"
date: 2010-02-15
forum: General Help
---

### Post by Zomaian on 2010-02-15
I am trying to use my Apple Remote Controller that came with my iMac 4.1. I did some research and on the Ubuntu site it said that its possible with a application called Infrared Remote Controller. It detected from the hardrive which version I had etc but than a error message appeared on the bottom saying:

**Warning:** Remote control daemon not running.

How can I activate this? I included a screenshot!

Thanks,
Bob

PS: Sorry for the bad red highlighting, I never use GIMP :P.

---

### Post by jweber30 on 2010-04-26
I'm having the same problem. I'm really new to linux but I'm doing my best. I have my hardware.conf file here:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Apple Mac mini USB IR Receiver"
REMOTE_MODULES="''"
REMOTE_DRIVER="macmini"
REMOTE_DEVICE="/dev/usb/hiddev0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="''"
REMOTE_LIRCD_ARGS="''"

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

# Receiver settings required by gnome-lirc-properties
RECEIVER_MODEL="Built-in\ IR\ Receiver\ \(0x8240\)"
RECEIVER_VENDOR="Apple"

# Remote settings required by gnome-lirc-properties
REMOTE_MODEL="A1156"
REMOTE_VENDOR="Apple"
```

---

