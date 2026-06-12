---
title: "problem with LIRC with pinnacle remote kit for mce and ubuntu 10.04"
date: 2010-06-01
forum: General Help
---

### Post by darklumen on 2010-06-01
Hi, I have very little knowledge of linux and I cant get my pinnacle remote kit for MCE working with LIRC.  I've managed to install LIRC and edit the config file so that it looks like this:

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Pinnacle Systems PCTV (pro) receiver"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="pinnacle_systems/lircd.conf.pctv"
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
LOAD_MODULES="lirc_dev lirc_mceusb2"

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

the lircd.conf has this on it

include "/usr/share/lirc/remotes/pinnacle_systems/lircd.conf.pctv"

If I restart the service it starts OK but when I try irw and press some keys I don't get anything... can anyone help?????

---

### Post by darklumen on 2010-06-03
ping :(

---

