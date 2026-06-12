---
title: "I KNOW ALOT OF PEOPLE POST THIS ! ( sorry in advance )"
date: 2010-11-16
forum: General Help
---

### Post by grahamz on 2010-11-16
ok 

Ushare installed 

I can see it on the 360 

but there is no files ? 

getting this error when starting ushare via  --            ushare -x

 

media@media-desktop:~$ ushare -x
Interface eth2 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See [http://ushare.geexbox.org/](http://ushare.geexbox.org/) for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.68:49201
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : home/media/xbox360
scandir: No such file or directory
Found 1 files and subdirectories.

Then it locks up you could say it doesn't give me an option to keep typing.. 

Ushare Config 


# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Media Server 

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth2
USHARE_IFACE=eth2

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=1337

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=home/media/xbox360

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=yes

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no


ALSO MY ETHO 2 IS RUNNING CUZ IM USING MY INTERNET ( IF IM CORRECT ? ) 

PLEASE HELP ! 

BEEN GOING AT THIS FOR 3 DAYS NOW LOL 

J

---

### Post by grahamz on 2010-11-17
Nobody huh

---

### Post by wilee-nilee on 2010-11-17
> **grahamz said:**
> Nobody huh

Don't have a clue myself but I do know that somewhere on the web some do, here is a link from the UF regrading this. Look at the dates of posts though to be up to date.
[http://ubuntuforums.org/showthread.php?t=632428](http://ubuntuforums.org/showthread.php?t=632428)

Found it with a search for a ushare forum you never know there may be one, but you will have to do the footwork.
[http://www.google.com/webhp?hl=en#hl=en&expIds=27606&xhr=t&q=ushare+forum&cp=10&pf=p&sclient=psy&site=webhp&aq=f&aqi=g4g-o1&aql=&oq=ushare+for&gs_rfai=&pbx=1&fp=e5790a4486b7f45f](http://www.google.com/webhp?hl=en#hl=en&expIds=27606&xhr=t&q=ushare+forum&cp=10&pf=p&sclient=psy&site=webhp&aq=f&aqi=g4g-o1&aql=&oq=ushare+for&gs_rfai=&pbx=1&fp=e5790a4486b7f45f)

---

### Post by grahamz on 2010-11-17
Thanks , but trust me iv done the footwork... I'm not giving up though.

---

### Post by shmup on 2010-11-22
I'm jealous that you can even see it on the desktop.

I've looked over many guides (most dating back a few years), and think I'm doing everything right, but clearly not.

I've made sure the port is open, and nearly everything else I can think of.

---

### Post by neoroses on 2010-11-22
I have had some very similar issues with ushare in the past and a few things that help me along the way are:

Giving your 360 and pc a local static ip. Forward ALL off the xbox live port and xbox network ports (TCP 80 UDP 88 TCP/UDP 53 TCP/UDP 3074) 

i realise this should not make a differance over a LAN but it seemed to work for me. Also name your server to somthing without spaces: "Usharexbox" or somthing along thoes lines. Put a "/" before home in > USHARE_DIR=home/media/xbox360

start with ```
sudo /etc/init.d/ushare start
```

if you have any port blocking things like mobloquer turn them off.

Make sure your xbox is OFF when starting ushare. and basicaly make sure you installed it following this

[HTML]http://ubuntuforums.org/showthread.php?t=848144&highlight=ushare+xbox360[/HTML]

this is the only method i have used successfully - fuppes is would reccomend these days but to be honist streaming to the xbox just seems very hit and miss some time! hope this helps pal

---

### Post by SlugSlug on 2010-11-22
Interface eth2 is down.
Recheck uShare's configuration and try again !


why have you set it to eth2?


can you post output of 
ifconfig

most likely needs to be eth0

---

### Post by grahamz on 2010-12-13
wow sorry iv been on holiday...

ifconfig
eth2      Link encap:Ethernet  HWaddr 00:1e:8c:82:8a:f5  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe82:8af5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369665776 (369.6 MB)  TX bytes:17398697 (17.3 MB)
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2376 (2.3 KB)  TX bytes:2376 (2.3 KB)

---

