---
title: "NomadIIMG Resurrection!"
date: 2011-09-16
forum: General Help
---

### Post by BcRich on 2011-09-16
Hi 
I'm trying to get my old Nomad II MG mp3 player to be recognized in ubuntu. I did have this working at one stage but I just don't remember how I managed to get it setup. I know that I required nomadII-utils-0.8 but checking again at source forge i see a couple of new files have appeared with version number greater than 0.8 [http://sourceforge.net/projects/nomadii/files/](http://sourceforge.net/projects/nomadii/files/)
one of the files seem to imply that there is now a gui for interfacing with the nomadII MG. 
Ubuntu definitely recognizes my Nomad as lsusb identifies it as
```
Bus 007 Device 004: ID 041e:4004 Creative Technology, Ltd Nomad II MG
```
I'd really appreciate some help on getting the device to mount so that I can transfer files to it from nautilus. There are some vague instructions in a readme file 
> 1. Get a Nomad II
2. Get a Motherboard with an usb controller
3. Install Linux
4. Install Kernel 2.2.17+backport USB or later or, of course, a kernel from the 2.4.x series.
5. Activate USB, UHCI or OHCI driver and don't forget USBDEVFS
6. Mount usbdevfs. Add the following line to /etc/fstab:
   none                    /proc/bus/usb           usbdevfs defaults               0 0
   Redhat 7.1 or later will mount this for you on boot.
7. Do mount -a
8. Get this wonderful tool (Oh, you already have it!)
9. Unpack it
10. Edit Makefile - Set USE_READLINE=1 (default) for command history and completion
                or  USE_READLINE=0 to deactivate this wonderful features.
            Set ENABLE_DEBUG=0 (default) for silent operation
            or  ENABLE_DEBUG=1 for packet dump. (You must also use --debug option to turn it on)
11. make
12. make install
13. man nomadii
14. Execute with nomadii
15. Enjoy 
but there is no makefile in any of the packages I've downloaded
[http://tenet.dl.sourceforge.net/project/nomadii/libnomadii/0.9-alpha/libnomadii-0.9-alpha.tgz](http://tenet.dl.sourceforge.net/project/nomadii/libnomadii/0.9-alpha/libnomadii-0.9-alpha.tgz)
[http://tenet.dl.sourceforge.net/project/nomadii/nomadii/0.9-alpha/nomadii-0.9-alpha.tgz](http://tenet.dl.sourceforge.net/project/nomadii/nomadii/0.9-alpha/nomadii-0.9-alpha.tgz)
[http://tenet.dl.sourceforge.net/project/nomadii/nomadii-gui/gnoii2-0.3-alpha3/gnoii2-0.3-alpha3.tar.gz](http://tenet.dl.sourceforge.net/project/nomadii/nomadii-gui/gnoii2-0.3-alpha3/gnoii2-0.3-alpha3.tar.gz)
I've also tried using gmtp to see if it's identified by gmtp but that doesn't seem to work either.
I'd really appreciate it if someone could help me get this device to mount like a drive in ubuntu.
Ubuntu Studio 10.10
Nomad II MG

---

