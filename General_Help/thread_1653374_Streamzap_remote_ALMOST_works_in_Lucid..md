---
title: "Streamzap remote ALMOST works in Lucid."
date: 2010-12-26
forum: General Help
---

### Post by martini1179 on 2010-12-26
EDIT: I should mention that I have a "new" Streamzap remote, made around 2010. Some peoples' "older" Streamzap remotes apparently work fine and say that the remote has changed and yet lirc hasn't kept up. 

I just bought a Streamzap remote for Lucid. I've read that it works flawlessly, out of the box, and even on Lucid. But I'm finding that this isn't completely true. 

I think I have some kind of configuration problem. I've run
```
irw
```
and I've gotten correct corresponding button events, so that part works. Also, gnome-lirc-properties is able to autodetect my remote. 

I've configured lirc 0.8.6 for the Streamzap upon insall, but left the IR receiver question blank, since there's no Streamzap option. Regardless, I've tried reconfiguring several times via ```
sudo dpkg-reconfigure lirc

```
to no avail. 

/etc/lirc/hardware.conf lists the following:
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Streamzap PC Remote"
REMOTE_MODULES="lirc_dev lirc_streamzap"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="streamzap/lircd.conf.streamzap"
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
```

/etc/lirc/lircd.conf lists:
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Streamzap PC Remote remote:
include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"

```

Any help would be greatly appreciated.

---

### Post by martini1179 on 2010-12-27
/bump

---

### Post by martini1179 on 2010-12-29
/bump

---

### Post by chrisinspace on 2011-01-15
I'm having the exact some problem.  A similar issue was being discussed [here]("http://ubuntuforums.org/showthread.php?t=1595018&page=7"), but I haven't found a solution in that thread yet.  I haven't tried the idea in post #65 yet, but I'm not sure if that's going to help the fact that some of my keys don't do anything at all.  This is really frustrating.  I bought this remote specifically because it had a good reputation for playing nice with lirc.

---

### Post by chrisinspace on 2011-01-15
Ok.  I re-read your post and realized that you stated what IS working, but not what ISN'T working.  What problem are you experiencing, exactly?

Here's my problem.  Everything looks like it should work.  The irw output is right on, but when I try to use the remote in XBMC, Boxee, or Hulu Desktop, the arrow keys work and volume + and - kind of work, but 'OK', 'exit', |<<, >>|, <<, >>, 'menu', and 'stop' don't.  It's the same all applications.

I also have a new Streamzap remote purchased in December 2010.  However, I'm using Maverick, not Lucid.

---

### Post by martini1179 on 2011-01-16
Basically, everything that I stated was working is the ONLY thing working. I can get output from the irw command, and when I press any button on the remote, the red light flashes on the receiver. That's it. 

With Lucid, there's a patch coming down the tubes in Lucid-proposed, which looks like it MIGHT address the issue: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/567512](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/567512)

But then again, you probably already have it installed and it's still not working. The problem is that lirc is not properly maintained. If you go on their site, [www.lirc.org](www.lirc.org), you'll see a 12-month gap between 0.8.6 (Lucid) and 0.8.7 (Maverick???). What version does Maverick have? I'd compile the latest (0.8.7) myself from source, but I'm pretty sure you already have it and are still having problems.

---

