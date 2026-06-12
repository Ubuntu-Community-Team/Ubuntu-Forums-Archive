---
title: "vmware wont run with new kernel."
date: 2006-06-23
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-06-23
Ever since I updated my kernel, vmware won't run. Does anyone know how to mke it run?

---

### Post by rickyjones on 2006-06-23
Download the new kernel sources (sudo apt-get install linux-headers) (I think that's the command).

Then you have to reconfigure vmware: sudo /usr/bin/vmware-config.pl

Accept the defaults and let it recompile the network card drivers.

Should work just fine after that :-).

Hope it helps!

-Richard

---

### Post by s_h_a_d_o_w_s on 2006-06-23
I tried it and I got:

(some boring text)

then:
Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.16-ck12/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. mo dules
make[1]: Entering directory `/usr/src/linux-2.6.16ck12'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-2.6.16ck12'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmmon.o': -1 Invalid module format
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by rbalfour on 2006-06-23
[QUOTE=rickyjones]Download the new kernel sources (sudo apt-get install linux-headers) (I think that's the command).

Then you have to reconfigure vmware: sudo /usr/bin/vmware-config.pl

Accept the defaults and let it recompile the network card drivers.

Should work just fine after that :-).

Hope it helps!

-Richard[/QUOTE]

$ sudo apt-get install linux-headers-`uname -r`

---

### Post by Lunar_Lamp on 2006-06-23
Thanks - that sorted my problems out also!

---

### Post by s_h_a_d_o_w_s on 2006-06-23
max@linuxrules:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.16-ck12

---

### Post by s_h_a_d_o_w_s on 2006-06-23
Is is that I need extra repos?

---

### Post by mbeierl on 2006-06-23
Based on the fact that your kernel is reporting 2.6.16-ck12, I would say you've got a custom compiled kernel.  How did you install this if you did not compile it yourself?

---

### Post by v79 on 2006-06-24
[QUOTE=Lunar_Lamp]Thanks - that sorted my problems out also![/QUOTE]

Afraid this isn't working for me at all. Installed the latest kernel headers (which automatically triggers vmware to do, em, something), but I still can't run VMPlayer:

```
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.
```

Is it my 64 bit kernel? 
$ uname -r
2.6.15-25-amd64-k8

Help!

---

### Post by lamego on 2006-06-24
vmware player is available on the ubuntu repos, it can be installed with:
```
sudo apt-get install vmware-player
```
I am running it with the latest Ubuntu kernel without problems.

---

### Post by siriusnova on 2006-06-24
[QUOTE=v79]Afraid this isn't working for me at all. Installed the latest kernel headers (which automatically triggers vmware to do, em, something), but I still can't run VMPlayer:

```
Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.
```

Is it my 64 bit kernel? 
$ uname -r
2.6.15-25-amd64-k8

Help![/QUOTE]

everytime you install or update to a new kernel you must rebuild your vmnet module.
First install build-essential via aptitude or synaptic
Then install linux-kernel-headers specific to your kernel ie amd64 or 386 etc..

then open a terminal and go to /usr/src/ directory 

"cd /usr/src"

then link the kernel header directory that is specific to your kernel, for example mine is 686 to a linux softlink

"sudo ln -s linux-headers-2.6.15-25-686 linux"

so now in that directory /usr/src/linux will point to the directory /usr/src/linux/kernel-headers-2.6.15-25-686 (in my case).

now in a terminal run

"sudo vmware-config.pl"

and follow the directions

---

### Post by Sheik Yerbouti on 2006-06-24
I too have been going through this. the real problem is VMware will not compile with a custom kernel. It compiles fine with tha latest stock Ubuntu kernel. However as advised on the Ubuntu studio webpage I went down the path of compiling a custom kernel with the real time preemption patch. Which works pretty much flawlessly for audio. However vmware vmmon kernel modules will not compile with it. 

There is a user created patch called vmware any any that is supposed to allow you to compile vmware modules with unsupported kernels available at [http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/). However looking at the readme [http://ftp.cvut.cz/vmware/readme.txt](http://ftp.cvut.cz/vmware/readme.txt) looks like it needs a refresh before it will work for me. I am running vmware server since it is free right now being in beta. Maybe I will try vmware player or something I dont know I will probably keep hacking at this because I really want this to work the realtime kernel is really worth it audio wise and also the latest Ubuntu kernel timer resolution is set too low for midi that is 2.6.16-25.

If you are running a 2.6.16 custom kernel and a vmware version listed in vmware any any give that a shot it should work in getting vmware compiled on a custom kernel.

Cheers

---

### Post by Sheik Yerbouti on 2006-06-24
Ok so here the deal vmware kernel modules will not run with a kernel that has the realtime preepmtion patch installed period. Not at least until vmware fixes this. Here's the straight dope from the kernel log when trying to load the vmmon kernel module.

vmmon: Unknown symbol rt_mutex_lock

So here's the dilema with the realtime kernel you get super low latency audio performance under jack for profesional audio work but you lose vmware. The stock ubuntu dapper kernel is far from ideal for audio but vmware works fine. So here's my somewhat ghetto solution that actually works. Just keep the stock kernel and the realtime kernel. Boot the the realtime kernel for audio work and the boot back into the stock kernel for gaming general usage and vmware. Of course there is the issue of my Nvidia kernel module not liking one kernel or the other depending on where it was compiled. But I work around this my having two xorg.conf files the one for my realtime audio kernel just use  the plain old non accelerated nv driver. The stock kernel uses the full blown nvidia hardware accelerated drivers. This works out fine because I don't need hardware accelerated open gl for audio work so no loss there. I just have two files /etc/X11/xorg.conf.rt <<realtime nv version /etc/X11/xorg.conf.ubu << stock version with nvidia driver. I just copy over which one I want to boot into and I am good to go. Hope this helps someone else

Cheers

---

### Post by v79 on 2006-06-25
[QUOTE=siriusnova]everytime you install or update to a new kernel you must rebuild your vmnet module.
First install build-essential via aptitude or synaptic
Then install linux-kernel-headers specific to your kernel ie amd64 or 386 etc..

then open a terminal and go to /usr/src/ directory 

"cd /usr/src"

then link the kernel header directory that is specific to your kernel, for example mine is 686 to a linux softlink

"sudo ln -s linux-headers-2.6.15-25-686 linux"

so now in that directory /usr/src/linux will point to the directory /usr/src/linux/kernel-headers-2.6.15-25-686 (in my case).

now in a terminal run

"sudo vmware-config.pl"

and follow the directions[/QUOTE]

I'm afraid that didn't work:

Firstly, there's no 'vmware-config.pl file:

$ vm
vmnet-bridge              vmnet-sniffer             vmware-config-network.pl
vmnet-dhcpd               vmplayer                  vmware-ping
vmnet-natd                vmstat
vmnet-netifup             vm-support

And vmware-config-network.pl asks lots of questions, the answer to which is always yes:

```
Selecting previously deselected package vmware-player-kernel-source.
Unpacking vmware-player-kernel-source (from .../vmware-player-kernel-source_2.6. 15.10-6_all.deb) ...
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.205.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] yes

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.114.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
```

This is kinda above my head. Certainly didn't have to do any of this when i first apt-get install vmware-player . Am I in over my head?

Ta

---

### Post by givré on 2006-06-25
Do you install vmware from the repo? if it is, install vmware-player-modules for the new kernel (ie 2.6.15-25)

---

### Post by gossea on 2006-06-26
Kernel module loader could not locate vmmon or vmnet modules, even after reboot and verification that modules had in fact been installed for the correct kernel version:

```

# modprobe vmmon
FATAL: Module vmmon not found.

```

Issued:

```

# depmod -a

```

All is working now:
```

# /etc/init.d/vmware-player start

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

```

---

### Post by eiamjw on 2006-10-12
I've followed the steps suggested here, but I don't have a /usr/bin/vmware-config.pl file

To be more specific, I ran:
$ sudo apt-get install linux-headers-`uname -r`
...
$ sudo /usr/bin/vmware-config.pl
sudo: /usr/bin/vmware-config.pl: command not found

I have kernel 2.6.15-27-386

---

### Post by at0mic on 2006-10-21
i have the same prob as v79 with x64 kernel

---

### Post by nlyric on 2006-11-01
Just wanted to take a minute and say thank you to everyone who posted on this page. I am running Mepis 6.0 with kernel 2.6.15-27-k7 and I was having problems with vmmon and vmnet not being found . The simlink solved the module not found error. But loading them was a different story. When I did modprobe vmmon I got "vmmon module is invalid format" and the same for vmnet. In desperation I did modprobe --force vmmon and that did the trick. Thanks again

---

### Post by cleentrax on 2006-11-01
](*,) 

latest Edgy generic kernel from the repos, and latest vmware-player from the repos. I can't get it to get through the configuration properly.

```
$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.37.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.44.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

/usr/share/doc/vmware-player/EULA: No such file or directory

Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

The file /usr/share/mime/packages/vmware.xml that this program was about to 
install already exists.  Overwrite? [yes] 


In which directory do you want to install the mime type icons? 
[/usr/share/icons] 
What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

The file /usr/share/pixmaps/vmware-server.png that this program was about to 
install already exists.  Overwrite? [yes] 

/usr/share/applications/vmware-server.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
/usr/share/applications/vmware-console-uri-handler.desktop: error: Categories values must be one of "Core", "Development", "Building", "Debugger", "IDE", "GUIDesigner", "Profiling", "RevisionControl", "Translation", "Office", "Calendar", "ContactManagement", "Database", "Dictionary", "Chart", "Email", "Finance", "FlowChart", "PDA", "ProjectManagement", "Presentation", "Spreadsheet", "WordProcessor", "Graphics", "2DGraphics", "VectorGraphics", "RasterGraphics", "3DGraphics", "Scanning", "OCR", "Photography", "Viewer", "Settings", "DesktopSettings", "HardwareSettings", "PackageManager", "Network", "Dialup", "InstantMessaging", "IRCClient", "FileTransfer", "HamRadio", "News", "P2P", "RemoteAccess", "Telephony", "WebBrowser", "WebDevelopment", "AudioVideo", "Audio", "Midi", "Mixer", "Sequencer", "Tuner", "Video", "TV", "AudioVideoEditing", "Player", "Recorder", "DiscBurning", "Game", "ActionGame", "AdventureGame", "ArcadeGame", "BoardGame", "BlocksGame", "CardGame", "KidsGame", "LogicGame", "RolePlaying", "Simulation", "SportsGame", "StrategyGame", "Education", "Art", "Construction", "Music", "Languages", "Science", "Astronomy", "Biology", "Chemistry", "Geology", "Math", "MedicalSoftware", "Physics", "Teaching", "Amusement", "Applet", "Archiving", "Electronics", "Emulator", "Engineering", "FileManager", "Shell", "ScreenSaver", "TeminalEmulator", "TrayIcon", "System", "Filesystem", "Monitor", "Security", "Utility", "Accessibility", "Calculator", "Clock", "TextEditor", "KDE", "GNOME", "GTK", "Qt", "Motif", "Java", "ConsoleOnly" (found "Application")
desktop-file-install created an invalid desktop file!
Unable to install the .desktop menu entry file. You must add it to your menus 
by hand.
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-10-generic/build/include] 

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in 
the "/tmp/vmware-config0" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by phatsteve on 2007-01-19
If it's any help , I had this problem until I installed the 'any-any-update' from [http://ftp.cvut.cz/vmware/](http://ftp.cvut.cz/vmware/)
(vmware-any-any-update105.tar.gz )

---

### Post by markba on 2007-02-10
It seems that the installed vmware kernel modues are not in sync. After loading the new modules  for 2.6.17.11 (they are available but not updated automatically), everything works fine.

```
uname -a
[INDENT]Linux lin11 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux[/INDENT]

# Search for installed kernel modules, kernel modules are NOT in sync!
dpkg -l | grep vmware | grep kernel
[INDENT]ii  vmware-player-kernel-modules               2.6.17.10                            vmware-player kernel module dependency packa
ii  vmware-player-kernel-modules-2.6.17-10     2.6.17.7-10.1                        vmware-player modules for Linux (kernel 2.6.[/INDENT]

# Remove vmware-player
sudo apt-get install vmware-player

# Search for available kernel modules
sudo apt-cache search vmware | grep modules
[INDENT]vmware-player-kernel-modules - vmware-player kernel module dependency package
vmware-player-kernel-modules-2.6.17-10 - vmware-player modules for Linux (kernel 2.6.17)
vmware-player-kernel-modules-2.6.17-11 - vmware-player modules for Linux (kernel 2.6.17)[/INDENT]

# Upgrading kernel modules
sudo apt-get install vmware-player-kernel-modules-2.6.17-11
sudo apt-get remove vmware-player-kernel-modules-2.6.17-10

# Re-install vmware-player, now vmware-player starts!
sudo apt-get install vmware-player

```

Note:
```
dpkg -l | grep vmware | grep kernel
[INDENT]ii  vmware-player-kernel-modules               2.6.17.10                            vmware-player kernel module dependency packa
ii  vmware-player-kernel-modules-2.6.17-10     2.6.17.7-10.1                        vmware-player modules for Linux (kernel 2.6.
ii  vmware-player-kernel-modules-2.6.17-11     2.6.17.7-11.1                        vmware-player modules for Linux (kernel 2.6.
[/INDENT]
```
As it turns out, installing vmware-player re-installs vmware-player-kernel-modules-2.6.17-10. Apparently this does not matter.
Also, vmware-player-kernel-modules seems to be bound to 2.6.17.10. Apparently this does not matter also.

My guess is that this is a package problem within vmware.

---

### Post by worapongni on 2007-03-14
I tried to do like you about package problem, it can work at that time. Unfortunately it does not work when I restart Ubuntu. Same problem occurs again. Any idea is appreciated.

I tried to do on modprobe, but it does not work either.

---

