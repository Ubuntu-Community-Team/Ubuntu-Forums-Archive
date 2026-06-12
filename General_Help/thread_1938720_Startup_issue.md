---
title: "Startup issue"
date: 2012-03-10
forum: General Help
---

### Post by astrobob.tk on 2012-03-10
From the moment Ubuntu loads & up to 7 minutes, the following happens:

1) in terminal, top shows the following two processes:

2948 astrobob  20   0 59524  18m  15m S    8  0.5   0:02.81 gnome-system-monitor                                                                                                                    
 2582 astrobob  20   0  119m  15m  10m D    2  0.4   0:02.70 /usr/lib/gnome-settings-daemon/gnome-settings-daemon

2) the system monitor shows: Selection_01 (in task bar; notice the high cpu usage) & image
3) hardisk makes a sound: maybe reading the contents ?

this happens at every login and stays up to 7 minutes after which all the above do not show anymore. I've been facing this for 6 months ++. Moreover, during these 7 minutes, whatever I try to open (e.g; nautilus, evince) takes time to open & then freezes for sometime then works normally.

Can you please help me figure this out & what's causing it & how to solve it ?

thanks

---

### Post by imachavel on 2012-03-10
you used top? it's hard to understand though, according to your output, those processes are each using less then 10% of the cpu. What model of computer are you using? How bad does the system crash? What processor how much ram etc. does your computer use?

---

### Post by astrobob.tk on 2012-03-10
> **imachavel said:**
> you used top? it's hard to understand though, according to your output, those processes are each using less then 10% of the cpu. What model of computer are you using? How bad does the system crash? What processor how much ram etc. does your computer use?

I always use top. Actually i discovered the above processes from top. The processes mentioned are the top processes using the cpu at login.

How exactly can I make things easier? I can reboot & check what ever helps in the process.

System crash? Well I did have an init problem a while ago: [http://ubuntuforums.org/showthread.php?t=1751541](http://ubuntuforums.org/showthread.php?t=1751541)
which I overcome using fsck.

Maybe the following threads I opened might give a help:
[http://ubuntuforums.org/showthread.php?t=1645330](http://ubuntuforums.org/showthread.php?t=1645330)
[http://ubuntuforums.org/showthread.php?t=1850263](http://ubuntuforums.org/showthread.php?t=1850263)

Laptop is Dell Studio XPS (plz see signature). Need any other details?

---

### Post by imachavel on 2012-03-10
well, the system monitor and daemons should be running at start up. Should they not? This is equivalent of windows ms config showing processes that should be running at start up. How to change selection of what runs at start up? I don't know, try:

sudo apt-get install startupmanager

(btw, now that you mention it, I'm getting some bugs also, can't seem to open synaptic package manager)

I should mention, it seems that your laptops both have processors clocked under 3.0 ghz, which might be a reason for bottlenecking. Does your computer actually crash in a hardware/software failure sort of way or just slow down? The laptop processors are under clocked to avoid over heating since laptops are much smaller then desk tops. You say your computer doesn't bluescreen/restart/log you out/give you a returned error message from any of these problems right?

anyway, try these other command line techniques as well:

free -tm
             total       used       free     shared    buffers     cached
Mem:          3024       2816        207          0        234       1594
-/+ buffers/cache:        988       2035
Swap:        32767          0      32767
Total:       35792       2817      32975

code:

sudo apt-get install startupmanager
[sudo] password for danel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  menu
Suggested packages:
  menu-l10n
The following NEW packages will be installed:
  menu startupmanager
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 570 kB of archives.
After this operation, 3,543 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe menu i386 2.1.45ubuntu1 [453 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/universe startupmanager all 1.9.13-5 [117 kB]
Fetched 570 kB in 5s (101 kB/s)          
Selecting previously deselected package menu.
(Reading database ... 331079 files and directories currently installed.)
Unpacking menu (from .../menu_2.1.45ubuntu1_i386.deb) ...
Selecting previously deselected package startupmanager.
Unpacking startupmanager (from .../startupmanager_1.9.13-5_all.deb) ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up menu (2.1.45ubuntu1) ...
Processing triggers for menu ...
Setting up startupmanager (1.9.13-5) ...
Processing triggers for menu ...
Processing triggers for python-support ...

code:

danel@danel-Dimension-4700:~$ free -tm
             total       used       free     shared    buffers     cached
Mem:          3024       2816        207          0        234       1594
-/+ buffers/cache:        988       2035
Swap:        32767          0      32767
Total:       35792       2817      32975
danel@danel-Dimension-4700:~$ sudo apt-get clean
danel@danel-Dimension-4700:~$ sudo apt-get clean
danel@danel-Dimension-4700:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
danel@danel-Dimension-4700:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danel@danel-Dimension-4700:~$ sudo apt-get update
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted TranslationIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/main Translation-en
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012) oneiric/restricted Translation-en
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 

Reading package lists... Done

---

### Post by imachavel on 2012-03-10
code:

danel@danel-Dimension-4700:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danel@danel-Dimension-4700:~$ sudo dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Rather than invoking init scripts through /etc/init.d, use the service(:cool:
utility, e.g. service acpid stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(:cool: utility, e.g. stop acpid
acpid stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(:cool:
utility, e.g. service acpid start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(:cool: utility, e.g. start acpid
acpid start/running, process 30294
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
 * Stopping web server apache2                                                   apache2: Could not reliably determine the server's fully  qualified domain name, using 127.0.1.1 for ServerName
 ... waiting .                                                           [ OK ]
 * Starting web server apache2                                                   apache2: Could not reliably determine the server's fully  qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing


do you get similar output at all? Let me know(p.s. I got some advice from those other threads you mentioned)

---

### Post by astrobob.tk on 2012-03-12
> **imachavel said:**
> well, the system monitor and daemons should be running at start up. Should they not? This is equivalent of windows ms config showing processes that should be running at start up. How to change selection of what runs at start up? I don't know, try:

sudo apt-get install startupmanager


Indeed, I guess so. But this is taking too long. 7 minutes?

I think you meant "Startup Applications" under Preferences instead. This controls the software that launch at startup, while what you indicated (startupmanager) is the boot manager (i.e; what OS is to boot by default & how much time the menu is waiting for you...)

> I should mention, it seems that your laptops both have processors clocked under 3.0 ghz, which might be a reason for bottlenecking. Does your computer actually crash in a hardware/software failure sort of way or just slow down? The laptop processors are under clocked to avoid over heating since laptops are much smaller then desk tops. You say your computer doesn't bluescreen/restart/log you out/give you a returned error message from any of these problems right?
Could you please elaborate more on this thing? Underclocked? Ubuntu underclocks? or the hardware is underclocked?

Sudden system crashes? No. But i do occasionally face the problem that the mouse pointer stops responding. I can't move it. It goes back to normal after a reboot.

Other than that, the only problem I faced is the "init" problem described in one of the threads & which has been (faced it quite a number of times) temporarily solved it using "fsck".

> 
anyway, try these other command line techniques as well:

free -tm
             total       used       free     shared    buffers     cached
Mem:          3024       2816        207          0        234       1594
-/+ buffers/cache:        988       2035
Swap:        32767          0      32767
Total:       35792       2817      32975
Already use it, but still learning:

```
$ free -tm
             total       used       free     shared    buffers     cached
Mem:          3987       3860        126          0         12       1435
-/+ buffers/cache:       2412       1574
Swap:         6761        102       6659
Total:       10748       3962       6785

```> 
sudo apt-get install startupmanager
Why install it if it is already present in the system by default? Anyways, I tried it & it is already the newest version. (I guess you have something messed up in ur system?)

> 
danel@danel-Dimension-4700:~$ sudo apt-get clean
danel@danel-Dimension-4700:~$ sudo apt-get clean
danel@danel-Dimension-4700:~$ sudo apt-get autoclean
danel@danel-Dimension-4700:~$ sudo apt-get autoremove
Already use these too!

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```Could you please explain what the command below did?

```
$ sudo dpkg-reconfigure -phigh -a
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 6720
gtk-update-icon-cache: Cache file created successfully.
 * Starting AppArmor profiles                                                                                                                                                                        Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                                                                                              [ OK ]
 * Reloading AppArmor profiles                                                                                                                                                                       Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                                                                                              [ OK ]
stop: Unknown instance: 
start: Job failed to start
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

atd stop/waiting
atd start/running, process 14987
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
avahi-daemon start/running, process 15061
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
Removing all DKMS Modules
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
Building only for 2.6.32-39-generic-pae
Building for architecture i686
Building initial module for 2.6.32-39-generic-pae
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-39-generic-pae/updates/dkms/

depmod.......

DKMS: install Completed.
update-initramfs: Generating /boot/initrd.img-2.6.32-39-generic-pae
 * Disabling additional executable binary formats binfmt-support                                                                                                                              [ OK ] 
 * Enabling additional executable binary formats binfmt-support                                                                                                                               [ OK ] 
update-alternatives: using /usr/bin/btcompletedir.bittorrent to provide /usr/bin/btcompletedir (btcompletedir) in auto mode.
update-alternatives: using /usr/bin/btdownloadcurses.bittorrent to provide /usr/bin/btdownloadcurses (btdownloadcurses) in auto mode.
update-alternatives: using /usr/bin/btdownloadheadless.bittorrent to provide /usr/bin/btdownloadheadless (btdownloadheadless) in auto mode.
update-alternatives: using /usr/bin/btlaunchmany.bittorrent to provide /usr/bin/btlaunchmany (btlaunchmany) in auto mode.
update-alternatives: using /usr/bin/btlaunchmanycurses.bittorrent to provide /usr/bin/btlaunchmanycurses (btlaunchmanycurses) in auto mode.
update-alternatives: using /usr/bin/btmakemetafile.bittorrent to provide /usr/bin/btmakemetafile (btmakemetafile) in auto mode.
update-alternatives: using /usr/bin/btreannounce.bittorrent to provide /usr/bin/btreannounce (btreannounce) in auto mode.
update-alternatives: using /usr/bin/btrename.bittorrent to provide /usr/bin/btrename (btrename) in auto mode.
update-alternatives: using /usr/bin/btshowmetainfo.bittorrent to provide /usr/bin/btshowmetainfo (btshowmetainfo) in auto mode.
update-alternatives: using /usr/bin/bttrack.bittorrent to provide /usr/bin/bttrack (bttrack) in auto mode.
update-alternatives: using /usr/bin/btcompletedirgui.bittorrent to provide /usr/bin/btcompletedirgui (btcompletedirgui) in auto mode.
update-alternatives: using /usr/bin/btdownloadgui.bittorrent to provide /usr/bin/btdownloadgui (btdownloadgui) in auto mode.
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

update-initramfs: Generating /boot/initrd.img-2.6.32-39-generic-pae
update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'

update-initramfs: Generating /boot/initrd.img-2.6.32-39-generic-pae
 * Stopping ClamAV daemon clamd                                                                                                                                                               [ OK ] 
 * Starting ClamAV daemon clamd                                                                                                                                                               [ OK ] 
 * Stopping ClamAV virus database updater freshclam                                                                                                                                           [ OK ] 
 * Starting ClamAV virus database updater freshclam                                                                                                                                           [ OK ] 
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.32-39-generic-pae
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.

```

much longer than yours. Do you understand it?

---

### Post by astrobob.tk on 2012-03-14
bump

---

### Post by astrobob.tk on 2012-03-15
> **dersd00 said:**
> You say your computer doesn't bluescreen/restart/log you out/give you a returned error message from any of these problems right?[IMG]<snip>[/IMG]

True, unless the following are related:

[http://ubuntuforums.org/showthread.php?t=1938726](http://ubuntuforums.org/showthread.php?t=1938726)
[http://ubuntuforums.org/showthread.php?t=1751541](http://ubuntuforums.org/showthread.php?t=1751541)

?

---

### Post by astrobob.tk on 2012-03-20
bump

---

### Post by astrobob.tk on 2012-03-29
Add to the first post the following fact:

sometimes the GUI falls down to the one in the attached image!

---

### Post by astrobob.tk on 2012-04-16
Just now, when I started the system and selected "Change Desktop Background" after gith click on the desktop, I got the following error:

---

### Post by ZekeGraal on 2012-04-16
> **astrobob.tk said:**
> Just now, when I started the system and selected "Change Desktop Background" after gith click on the desktop, I got the following error:

The only thing I get out of that message is that another program is trying to manage something. How old is your install? Maybe something was left in from a previous Ubuntu version and is conflicting? Have you tried to install gnome-shell or KDE or another type of window management system?

---

### Post by astrobob.tk on 2012-04-16
> **ZekeGraal said:**
> The only thing I get out of that message is that another program is trying to manage something. How old is your install? Maybe something was left in from a previous Ubuntu version and is conflicting? Have you tried to install gnome-shell or KDE or another type of window management system?

As a matter of fact, it was a fresh install but I guess the problem is that I have several desktop environments installed (fluxbox, openbox, blackbox, lxde but not KDE).

Previously I had problems with gnome conflicting with one of the  environments. Actually it is this thread: [http://ubuntuforums.org/showthread.php?t=1851597](http://ubuntuforums.org/showthread.php?t=1851597)

Might be related? If so why don't each environment use its own software & share the common stuff with other environments?

thanks

---

### Post by ZekeGraal on 2012-04-19
> **astrobob.tk said:**
> As a matter of fact, it was a fresh install but I guess the problem is that I have several desktop environments installed (fluxbox, openbox, blackbox, lxde but not KDE).

Previously I had problems with gnome conflicting with one of the  environments. Actually it is this thread: [http://ubuntuforums.org/showthread.php?t=1851597](http://ubuntuforums.org/showthread.php?t=1851597)

Might be related? If so why don't each environment use its own software & share the common stuff with other environments?

thanks

That would most likely be the problem. If you don't use some of the environments, remove them and make sure you run ```
sudo apt-get autoremove
``` when it is complete. That will remove any packages no longer needed by any applications on the system.

As for why; it's Linux. All the Linux distributions run on the same bones and drivers (most of the time), and in Ubuntu's case, a Debian based Linux. All the workspace managers rely on Debian's base, and if more than one is installed they will fight to try and control your desktop and windows.

Even if you login to Unity, having KDE or another manager system on your system will still run its processes; thus conflicting with the environment you are actually running at the time.

Hope this clears things up! 
~Zeke

---

### Post by astrobob.tk on 2012-04-24
> **ZekeGraal said:**
> That would most likely be the problem. If you don't use some of the environments, remove them and make sure you run ```
sudo apt-get autoremove
``` when it is complete. That will remove any packages no longer needed by any applications on the system.

As for why; it's Linux. All the Linux distributions run on the same bones and drivers (most of the time), and in Ubuntu's case, a Debian based Linux. All the workspace managers rely on Debian's base, and if more than one is installed they will fight to try and control your desktop and windows.


I did remove al environments but the problem persists!!

> **ZekeGraal said:**
> 
Even if you login to Unity, having KDE or another manager system on your system will still run its processes; thus conflicting with the environment you are actually running at the time.


I think that's a negative :S Hope this could be fixed in the future.

---

