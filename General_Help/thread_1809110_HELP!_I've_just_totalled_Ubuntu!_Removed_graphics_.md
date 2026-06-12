---
title: "HELP! I've just totalled Ubuntu! Removed graphics package (lib7??)"
date: 2011-07-21
forum: General Help
---

### Post by demonboy on 2011-07-21
Stupid, stupid, stupid me! Whilst trying to install scanner software I stupidly uninstalled a vital package to the operation of Ubuntu and now I can't boot up. 'Embarrassing' doesn't even come close to describing how I feel :(

The package was lib-something, with a 7 in the name, and has something to do with graphics.

I'm not competent enough to troubleshoot myself so I'm looking for some guidance. What's the procedure here? Bear in mind I can't print out terminal messages as I'm on a different computer. 

Can anyone tell me what package it was and how best to fix this situation? Any pointers gratefully received as I'm sitting on someone else's computer to type this message.

Thanks in advance.

---

### Post by camaron1 on 2011-07-21
How far do you get in the booting process?

---

### Post by demonboy on 2011-07-21
On standard boot-up it comes up with:

> Ubuntu is running in low graphics mode.
Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.

I then click 'OK' and have some options:

> Run in low graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login
Restart X

**Run in low graphics mode for just one session**
Comes up with a window that says 'Stand by one minute while the display restarts...I click 'OK' and the Ubuntu logo appears with the flashing dots and just hangs.

**Reconfigure Graphics**
Gives me three options:
> Use default generic configuration
Create new configuration for this hardware
Use your backed-up configuration
Clicking on any of these options does nothing, it just gets caught in a loop on this window, so I click 'Cancel' instead.

**Troubleshoot The Error**
Returns options to review or edit the configuration log files etc. I don't know what I am doing here so I leave them. 
[B]
Exit To Console Login[/B]
Now I input username and password and I have a whole screen like Terminal. Dunno what to do here!

Does that help?

---

### Post by camaron1 on 2011-07-21
From the console try

```
sudo apt-get install ubuntu-desktop
```

this may re-installed the missing packages

Good luck

---

### Post by demonboy on 2011-07-21
Yes, but I need to be online to do that. The only option I have to type terminal commands is after booting up in 'console login' mode, and if I do that I'm not online.

Isn't there a way of repairing the install using a USB boot-disk or something? I've inserted a USB-bootable Ubuntu installation but when I boot up there doesn't appear to be an option to 'repair', only 'install'. Should I attempt the 'install' option and hope that it gives me the option to repair?

---

### Post by ajgreeny on 2011-07-21
You could just use the keyboard shortcut for a terminal (Ctrl+Alt+T) and run the command that way.

Or from the grub menu (hold shift after POST if you don't normally see the  menu) choose recovery mode.  I think you get the option to startup a cli  with network connection, which would then let you run the command  ```
apt-get install ubuntu-desktop
```No sudo needed from recovery  mode.

---

### Post by demonboy on 2011-07-21
I'm not sure I understand. I can't run Terminal because I can't boot up Ubuntu and I can't run the command you suggest because I can't get online... unless there's something I'm missing in your instructions?

If I choose recovery mode I have an option to 'drop to shell with networking' or somesuch but when I run your command it is failing because I'm not getting online.

---

### Post by nothingspecial on 2011-07-21
Can you get a wired connection somehow?

---

### Post by demonboy on 2011-07-21
Yes I can. I'm plugged in to my father's BT router. How do I go about getting online from terminal?

---

### Post by nothingspecial on 2011-07-21
Should be automatic with a wire connection

can you ping the router?

Think bt hubs default is 192.168.1.1

```
ping 192.168.1.1
```

---

### Post by nothingspecial on 2011-07-21
By the way, did you remove the package with apt-get? because if you did, there should be a record of it

```
cat /var/log/apt/history.log
```

---

### Post by demonboy on 2011-07-21
OK, the router is 192.168.1.254, which I can ping. However once I do that it gets caught in a loop and just keeps printing that it returns 64 bytes from the router, changing the icmp_reg number. (How do I break out of this?)

And I removed the package via Software Centre.

---

### Post by nothingspecial on 2011-07-21
Ctrl-C

Ok so you're are online. I'm guessing you are moving from computer to computer here or booting into windows to reply if you have a dual boot.

You think you could work with a text browser?

---

### Post by nothingspecial on 2011-07-21
Just discovered that software center is included in that log. (good to know)

Can you find what package you removed?

---

### Post by demonboy on 2011-07-21
I have two computers in front of me so I don't have to keep rebooting. Of course the problem is that I can't echo here what is being printed out on my computer but after running your 'cat' command I got a huge long list of results with no line breaks. They include:

> libcanberra-gtk0:i386 (0.28-0ubuntu3), imagemagic etc etc

It then ends with:

> Error:Sub-process /usr/bin/dpkg exited unexpectedly
Enf-date: 2011-07-21 10:12:00

Start-Date 2011-07-21 10:53:21
Comandline: apt-get install -f
Remove: libnunit2.4-cil:i386 (2.4.7+dfsg-6)
End-Date: 2011-07-21 10:53:31

However this may be a bit misleading as I did uninstall one package after my balls-up. I ran apt-get update and it came back with the failed updates and then a final 'remove this package?', to which I said 'yes'. So I think that last one is that package. How do I scroll back up that massive long list to get to the previous uninstalled package?

---

### Post by nothingspecial on 2011-07-21
use less instead of cat

by default less starts of the beginning of the file, so press End then scroll up.

---

### Post by demonboy on 2011-07-21
Hmmm, well it doesn't actually list the one package I last uninstalled, instead it lists all the other packages that that one package uninstalled. I can't begin to retype the list but it starts:

> Remove: libfolks-telepathy22:i386 (0.4.2-0ubuntu1), resapplet:i386 (0.0.7+cvs2005.09.30-0ubuntu5), sane-utils...

The list is at least two full screens-worth.

If I can get online can I not just do an apt-get update?

---

### Post by nothingspecial on 2011-07-21
You can do update, but you may need to install the actual package. The log should be in time order, so the package you removed should be near the end.

---

### Post by demonboy on 2011-07-21
OK, I think the package was 'libltdl7'. Can you see if this appears in Ubuntu Software Centre?

So I can hit the router but I'm not connected to the internet. How do I do that, and how do I reinstall that package?

And how do I break out of that 'less' command?

BTW - thank you for your patience and help so far!

---

### Post by nothingspecial on 2011-07-21
> **demonboy said:**
> 

and how do i break out of that 'less' command?



q

---

### Post by nothingspecial on 2011-07-21
You didn't want to remove that.

Try ```
sudo dhclient
```

```
sudo apt-get update && sudo apt-get install libltdl7
```

---

### Post by demonboy on 2011-07-21
It runs through a whole list of 'Ign [http://.](http://.)..', and then fails to fetch anything. I'm guessing I'm not online still, despite the 'dhclient' command. At no point has it asked me for a WEP password.

---

### Post by nothingspecial on 2011-07-21
> **demonboy said:**
> It runs through a whole list of 'Ign [http://.](http://.)..', and then fails to fetch anything. I'm guessing I'm not online still, despite the 'dhclient' command. At no point has it asked me for a WEP password.

You don't need a password if you're plugged right in.

```
sudo ifconfig eth0 up
sudo dhclient
```

Then try again.

---

### Post by holycow131415 on 2011-07-21
> **demonboy said:**
> It runs through a whole list of 'Ign [http://.](http://.)..', and then fails to fetch anything. I'm guessing I'm not online still, despite the 'dhclient' command. At no point has it asked me for a WEP password.

WEP is for wireless, you need to be hard wired into the router to make it easier on yourself. You said you were wired into the router earlier.

---

### Post by demonboy on 2011-07-21
Correct. I haven't hard-wired for a very long time.

When I try the eth0 up command it returns a > SIOCSIFADDR: No such device
up: ERROR while getting interface flags: No such device...etc etc

When I 'ifconfig' it comes back with eth0, eth1 and lo, and all have similar outputs:

> eth0    Link encap:Ethernet hWaddr 78:ac:c0.....
inet6 addr: f......
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1546 errors:0 dropped:0 overruns:0 frame:0
TX packets:613...etc as above
collisions:0...
RX bytes:318951 (318.9 KB) TX...
Interupst: 40 Base address:0x6000

---

### Post by nothingspecial on 2011-07-21
Try eth1

---

### Post by demonboy on 2011-07-21
I tried all three - eth0, eth1 and lo.

---

### Post by nothingspecial on 2011-07-21
At this point I would try restarting with the wire plugged in. You are not going to get a desktop.

Press Ctrl - Alt - F1 (together) to get to a console, then try updating and installing ubuntu-desktop.

I just had a look what that package removes, it's quite a long list

```
aisleriot brasero brasero-cdrkit compiz compiz-gnome empathy
  evolution-indicator evolution-plugins gbrainy gdm gdm-guest-session
  gnome-applets gnome-control-center gnome-media gnome-orca gnome-panel
  gnome-panel-bonobo gnome-power-manager gnome-screenshot gnome-session
  gnome-session-canberra gnome-settings-daemon gnome-user-share guile-1.8-libs
  gvfs-backends hplip imagemagick indicator-applet indicator-applet-appmenu
  indicator-applet-complete indicator-applet-session indicator-sound
  libbonoboui2-0 libbrasero-media1 libcanberra-gtk-module libcanberra-gtk0
  libcanberra-pulse libcanberra0 libevolution libgail-gnome-module libgnome2-0
  libgnome2.24-cil libgnomeui-0 libgphoto2-2 libgphoto2-port0 libltdl-dev
  libltdl7 libmagickcore3 libmagickcore3-extra libmagickwand3
  libmetacity-private0 libpanel-applet2-0 libsane libsox-dev libsox-fmt-all
  libsox-fmt-alsa libsox-fmt-ao libsox-fmt-base libsox-fmt-ffmpeg
  libsox-fmt-mp3 libsox-fmt-oss libsox-fmt-pulse libsox1b metacity
  nautilus-sendto-empathy pulseaudio pulseaudio-esound-compat
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  python-gnome2 python-pyatspi sane-utils shotwell simple-scan sound-juicer
  sox tomboy transmission-gtk tsclient ubuntu-desktop ubuntuone-client-gnome
  unity
```

Ouch

---

### Post by mokrates on 2011-07-21
* lo is wrong, it's the loopback interface.
* dhclient without any parameters should try all interfaces
* you said earlier, you could ping your router, that should mean, that your are, in fact, already online

---

### Post by ajgreeny on 2011-07-21
One possible way out could be to download the Alternate Install CD from
 [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) 
and use that as your software source, not possible with a live CD unfortunately.

Or at least, it did not used to be possible with a live CD;  has anything changed in that regard?

---

### Post by demonboy on 2011-07-21
Again, correct. I didn't think it was updating but it was. 

Anyway, updating desktop worked and all appears to be back to normal. Phew! Thank you all, specifically 'nothingspecial'. You've saved my bacon and I really appreciate it.

---

### Post by mokrates on 2011-07-21
the good thing about linux is: most times, you can acutally repair it. try that with a windows box :)

---

### Post by nothingspecial on 2011-07-21
Glad to here it's fixed.

---

