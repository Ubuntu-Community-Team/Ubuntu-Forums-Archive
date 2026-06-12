---
title: "linux does not recocnize camera"
date: 2009-12-05
forum: General Help
---

### Post by dansar99 on 2009-12-05
Hi....I have a Kodak LS443 camera with dock.   Why doesn't Ubuntu recognize it?  I have a dual boot system and the camera works fine on XP but Ubuntu wont even recognize that it's connected.   Dan

---

### Post by cariboo on 2009-12-05
Could post the output of:

```
dmesg | tail -n15
```

just after you have plugged your camera in. THe above command needs to be run in a terminal. This will tell us if and how your camera is detected.

---

### Post by dansar99 on 2009-12-05
here it is..Dan

   29.581293] __ratelimit: 3 callbacks suppressed
[   29.581302] type=1505 audit(1260043518.016:12): operation="profile_replace" pid=827 name=/usr/share/gdm/guest-session/Xsession
[   29.586633] type=1505 audit(1260043518.020:13): operation="profile_replace" pid=828 name=/sbin/dhclient3
[   29.587631] type=1505 audit(1260043518.020:14): operation="profile_replace" pid=828 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   29.608260] type=1505 audit(1260043518.044:15): operation="profile_replace" pid=828 name=/usr/lib/connman/scripts/dhclient-script
[   29.627960] type=1505 audit(1260043518.060:16): operation="profile_replace" pid=829 name=/usr/bin/evince
[   29.680162] type=1505 audit(1260043518.116:17): operation="profile_replace" pid=829 name=/usr/bin/evince-previewer
[   29.694163] type=1505 audit(1260043518.128:18): operation="profile_replace" pid=829 name=/usr/bin/evince-thumbnailer
[   29.720938] type=1505 audit(1260043518.156:19): operation="profile_replace" pid=831 name=/usr/lib/cups/backend/cups-pdf
[   29.722130] type=1505 audit(1260043518.156:20): operation="profile_replace" pid=831 name=/usr/sbin/cupsd
[   29.747038] type=1505 audit(1260043518.180:21): operation="profile_replace" pid=834 name=/usr/sbin/tcpdump
[   31.816153] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   31.816492] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.117103] usb 1-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   42.408036] eth0: no IPv6 routers present

---

### Post by dansar99 on 2009-12-05
bump

---

### Post by dansar99 on 2009-12-05
bump

---

### Post by fluffman86 on 2009-12-05
While Ubuntu recognizes my camera just fine, it is slow as molasses.  I find a USB card reader to be much faster.  Maybe you should drop $5 on one?  

If that's not an option, try installing picasa (there's an Ubuntu/Debian .deb file available).

Also, my camera shows up as a standard USB drive.  I guess you've looked in the Places menu?

---

### Post by dansar99 on 2009-12-05
yes...if I put a flash drive in a usb it recognizes it..but it does not recognize the camera.  Dan

---

### Post by dansar99 on 2009-12-06
anyone have a clue?  Dan

---

### Post by amturnip on 2009-12-06
> **dansar99 said:**
> Hi....I have a Kodak LS443 camera with dock.   Why doesn't Ubuntu recognize it?  I have a dual boot system and the camera works fine on XP but Ubuntu wont even recognize that it's connected.   Dan

Reboot.  Then skip the dock; plug the camera directly into the computer.

If that still doesn't work, please boot up the computer (without the camera connected) and post the results of the lsusb command before, and half a minute after, plugging in the camera.  (Not the dock.)

---

### Post by dansar99 on 2009-12-06
Unfotunately, there is no way to hook the camera to the usb w/o the dock . I'd need need a cable with an end that would fit into the camera like it fits into the dock.  Dan

---

### Post by deathbyswiftwind on 2009-12-06
Your best bet would be to spend the few bucks and buy one of the usb card readers if you can. I know its not the best but it would be the easiest to do and probably the most simple work around. Or if need be you could always vm windows that would probably work.

---

### Post by dansar99 on 2009-12-06
> **deathbyswiftwind said:**
> Your best bet would be to spend the few bucks and buy one of the usb card readers if you can. I know its not the best but it would be the easiest to do and probably the most simple work around. Or if need be you could always vm windows that would probably work.

I have a dual boot system on an old computer. I'm just trying to decide if I should buy a new computer with Linux installed but it looks like Windows 7 is going to be the choice. Stuff just doesn't work as well in Linux as Windows.  Dan

---

### Post by dansar99 on 2009-12-07
Anyone have a clue?  Dan

---

### Post by yaaarrrgg on 2009-12-29
> **dansar99 said:**
> Unfotunately, there is no way to hook the camera to the usb w/o the dock . I'd need need a cable with an end that would fit into the camera like it fits into the dock.  Dan

I've used a Kodak Easyshare dx7440.  It comes with a dock, but also has a option for a direct usb connection on the side of the camera.  

If yours doesn't have that option, it's probably going to be hard to get the camera to work through through the dock.  Since Kodak may  use a proprietary interface for that (not ptp/usb).  

Generally I would not recommend Kodak for digital cameras.  Kodak made good SLR cameras and film but they really aren't a computer/digital company.  They are old school.  So far I've had the best experience with Sony.

---

### Post by Girya on 2009-12-30
I've got the same problem with the camera I got for christmas. here's the work around I've got going:

install gphoto2: a command line app that works with my camera a Kodak easy share z915

```
$sudo apt-get install gphoto2
```


```
sudo killall gvfs-gphoto2-volume-monitor
```

This stops the default application from starting when you hook up the camera.

plug in your camera

fire up a terminal and cd into your photo directory or whereever you want the picts downloaded to.

type this command at the command line and that should download your pictures into the current directory.


$ gphoto2 --get-all-files

Sorry if this is a fast howto but I'm late to work, I'll try to post a better and more perm. fix with a script when I get home. hope this works for you.

kevin

---

