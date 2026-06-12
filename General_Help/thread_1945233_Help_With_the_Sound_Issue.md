---
title: "Help With the Sound Issue"
date: 2012-03-22
forum: General Help
---

### Post by kojiromusashi on 2012-03-22
Hi, Im just a newbie (first time to post here and new in Linux).

We have 5 new system that boots only in USB flash drive where the image of Linux version 2.6.38-13-generic is installed or copied. At first it was ok no problem at all. So we decided to copied it on the other usb flash drive (8gb) and when testing the systems there is no sound no mic. So I've tried a different headset w/ mic and it is ok. I test the previous headset on the other machine it is ok. I've found out that we need to unplug and replug the headsets in all the system where it boots in usb to make it work. When I tried to check the alsamixer this is what i get : 

cannot load mixer controls: Invalid argument



Any information on this issue? Any help would be much appreciated.

still no luck. Here are other info that I've got when trying to sort this : 

pulseaudio -v --log-target=stderr
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.22-24-g67d18
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is d61a1e846a96563bbdb64e6400000006.
I: main.c: Session ID is d61a1e846a96563bbdb64e6400000006-1332729292.807487-1230008528.
I: main.c: Using runtime directory /home/onlineme/.pulse/d61a1e846a96563bbdb64e6400000006-runtime.
I: main.c: Using state directory /home/onlineme/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.22/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

Thank you.

---

