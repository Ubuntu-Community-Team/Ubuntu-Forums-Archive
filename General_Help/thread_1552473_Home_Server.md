---
title: "Home Server"
date: 2010-08-13
forum: General Help
---

### Post by ubit on 2010-08-13
Hi,

i am currently planning a home server which should serve mainly as a file server for office and image processing. Clients are 3 Windows PCs (2*XP, 1*Vista 64). We must use Windows because photoshop does not run smoothly on ubuntu :-( (No: Gimp is NOT an option *g*).

The server should do:
- file server via Samba and Gigabit-Ethernet
- small webserver with a local wiki for storing manuals, drivers, information about insurences and contracts etc
- a small firebird database for the image database imabas
- possbily a document management (agorum core) - i have to experiment with such a system before we can go to "production level"
- printserver
- media streamer
- digital recording of dvb-t video (and streaming)
- giving remote access via xming/xdmcp to "play" a little with linux

I tried most of those functions on an old athlon system and found that ubuntu should do the job. I want to use the desktop version although it is a server - just because of convenience with remote access via xming and ease of configuration with local access.

While i was testing i noticed that the standard energy saving of ubuntu is a mess. I copied an external drive to the internal disk while i configured hibernation after a couple of minutes inactivity. The system went to s4 even if the copy was in full process. This is not what i have expected.

For "my" server i want another strategy:

1. The server should be startet from s4 (or s5) via Wake-On-Lane from the clients if the user decides to use the server. No problem here. Testet and works.
2. The system should shut down if there is "no activity"

Activity is therby defined as:

- arp has more entries than the dsl-router. That is there are still clients up and running
- printer is active/has jobs and is working (eg. NOT out of paper)
- no one is logged in into the system (locally or via xdmcp)
- the webserver/wiki got no access for a defined amount of time

Any ideas what else should the system prevent from go to sleep?

Additionally the clients should be able to tell the server "i don't need you anymore". Then this client should be ignored in arp-checking.

Is there any script out there that does (nearly) what i want? Or do i have do code such a script by myself?

Is there any application for Windows that is able to check if the server is up and running in the system tray with a small, coloured symbol? Would be nice.

Any comments to the planned hardware of the system?

- Mainboard MSI 785GM-E51
- CPU AMD Athlon II X3 435
- Harddisk Samsung SpinPoint F2EG Desktop Class HD154UI (2x, software raid 1)
- power supply Be quiet! Pure Power BQT L7-300W 
- Kingston ValueRAM -2GB (2 x 1GB) -  DDR3 - 1333 MHz - PC3-8500 - CL9

This into a cheep box from a local shop should give (more than) enough power for the planned software.

Is there another ubuntu-kind distribution that is better suited for my plans? The system should do the file-server-job fast and it should use as less electric power as possible. Power-Saver-Add-Ons from the mainboard-manufactures are only for windows :-( Any comparable software for linux with amd processors to clock down during idle?

Ciao, Udo

---

