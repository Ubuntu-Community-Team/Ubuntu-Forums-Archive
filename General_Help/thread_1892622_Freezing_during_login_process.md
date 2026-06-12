---
title: "Freezing during login process"
date: 2011-12-08
forum: General Help
---

### Post by sea_disk on 2011-12-08
Hi there, 
 
I have a problem with my relatively new installation of Kubuntu 11.10.

I was restarting my computer a few days ago the usual way via Kickoff>Leave>Restart.
 
Upon clicking Restart, the logout music played like normal and then everything except the mouse cursor just froze. I left it for about 15 minutes and when I returned it was still frozen. 

I then pressed the power button once and Kubuntu shutdown like normal. When I booted back up later I got to my login screen again like normal, typed my username and password and then it just froze again just before loading the desktop. There was nothing onscreen just the login splash and that's it. 
It was completely frozen again except the mouse cursor. I have checked lots of other posts and threads and they all seem to deal with temporary or occasional freezing, mine freezes at the same point every time and I then have to shutdown by pressing the power button once.

I am now using an installation of MEPIS I was testing until I can get Kubuntu working again.

Any help would be much appreciated!!

---

### Post by maverickaddicted on 2011-12-08
See this - 

[http://ubuntuforums.org/showthread.php?t=1081990](http://ubuntuforums.org/showthread.php?t=1081990)
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3107160.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3107160.0)

---

### Post by sea_disk on 2011-12-08
Thanks for replying.

I tried everything in those posts and I still have this problem.

I tried sudo startx and the NVIDIA logo showed like normal and then the screen went black.

I don't think this is an NVIDIA related problem because it started when I had the default Kubuntu driver (nouveau) installed.

I installed the NVIDIA driver via the console login last night hoping it would fix the problem but it obviously didn't.

Any further help would be much appreciated!!

---

### Post by sea_disk on 2011-12-08
OK, I have an update.

I found this in /var/log/kdm.log:


X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux xxxx-laptop 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=b4c09b6e-730e-4e84-a445-4dcd31ecfbe2 ro quiet splash vt.handoff=7
Build Date: 19 October 2011  05:09:41AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec  8 19:10:31 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) Failed to load module "nv" (module does not exist, 0)
klauncher(1268) kdemain: No DBUS session-bus found. Check if you have started the DBUS server. 
kdeinit4: Communication error with launcher. Exiting!
kdmgreet(1260)/kdecore (K*TimeZone*): KSystemTimeZones: ktimezoned initialize() D-Bus call failed:  "Not connected to D-Bus server" 

kdmgreet(1260)/kdecore (K*TimeZone*): No time zone information obtained from ktimezoned 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0308600744/.config/ibus/bus
 ddxSigGiveUp: Closing log


Any ideas anyone?

---

### Post by bluexrider on 2011-12-08
looks like

(EE) Failed to load module "nv" (module does not exist, 0)

Nvidia issue?? 

this may help

[http://ubuntuforums.org/showthread.php?p=10563728](http://ubuntuforums.org/showthread.php?p=10563728)

---

### Post by sea_disk on 2011-12-08
Thanks for replying.

I doubt that it's an NVIDIA related issue because I only installed the proprietary NVIDIA drivers last night thinking it might fix the problem. I've had this problem for the last few days.

Any more ideas?

---

### Post by sea_disk on 2011-12-08
Another update:

I tried launching plasma-desktop via the command line and got:

plasma-desktop(1603): KUniqueApplication: Cannot find the D-Bus session server:  "Unable to autolaunch a dbus-daemon without a $DISPLAY for X11"

plasma-desktop(1602): KUniqueApplication: Pipe closed unexpectedly.

Any ideas anyone?

---

### Post by maverickaddicted on 2011-12-09
> **sea_disk said:**
> Another update:

I tried launching plasma-desktop via the command line and got:

plasma-desktop(1603): KUniqueApplication: Cannot find the D-Bus session server:  "Unable to autolaunch a dbus-daemon without a $DISPLAY for X11"

plasma-desktop(1602): KUniqueApplication: Pipe closed unexpectedly.

Any ideas anyone?

This is not exactly the same forum, but will give you general idea about the messages.

[http://forums.debian.net/viewtopic.php?f=5&t=39216](http://forums.debian.net/viewtopic.php?f=5&t=39216)

---

### Post by sea_disk on 2011-12-09
It's OK now I wiped the partition and reinstalled everything so I'm back up and running again!!:)
Thanks anyway to maverickaddicted and bluexrider for the help.
Much appreciated!!

---

### Post by crackpotfox on 2011-12-09
ok, thanks for all the help... since i have had other problems that are also unresolved, and this has no work in it at all, I will just reinstall Kubuntu.

Thanks again!

---

### Post by sea_disk on 2011-12-09
> **crackpotfox said:**
> ok, thanks for all the help... since i have had other problems that are also unresolved, and this has no work in it at all, I will just reinstall Kubuntu.

Thanks again!

Well I'm sorry if it bothers you that I just gave up and reinstalled Kubuntu but I needed my system to work ASAP and I didn't have the time to keep investigating the problem.

---

