---
title: "Configuring LIRC to use Receiver and Remote"
date: 2012-03-23
forum: General Help
---

### Post by Clarifon on 2012-03-23
Hi guys,

Firstly, great forum you guys are running here. I am new to the whole linux thing and I've found a couple of answers on here that I was looking for.

My issue is that I'm struggling with LIRC to correctly identify my receiver and remote for use with XBMC.
I am using a Compro K300 IR USB receiver that I got with a remote.
For a remote I am using the Logitech Harmony 900

Now I know that there is no settings currently for the 900 so I was thinking of just using the Harmony1 for settings as the two are pretty similar but for some reason this won't work at all.

My hardware.conf file is

[PHP]# /etc/lirc/hardware.conf
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
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

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
START_LIRCMD=""[/PHP]Does anyone perhaps have any experience with this or could point me in the right direction?
I have looked at this post [http://ubuntuforums.org/showthread.php?t=1357762](http://ubuntuforums.org/showthread.php?t=1357762)
but not too sure as I get errors when trying to run that irrrecord command

---

### Post by Clarifon on 2012-03-27
*Bump*

Managed to get the receiver up and running and it receives the signal fine from the Compro remote when it's configured as a Windows MCE general receiver etc, however when I use the Harmony it doesn't want to work correctly. 

There are key mappings for the Harmony 1, but not too sure if I should use these. For now I have to have the keyboard with me on the couch and it's reception isn't all that great... :confused:

---

