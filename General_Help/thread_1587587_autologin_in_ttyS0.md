---
title: "autologin in ttyS0"
date: 2010-10-03
forum: General Help
---

### Post by aaronshepard on 2010-10-03
I am setting up a system to receive commands from an audio device that sends out acsii commands through a serial port. The plan is to have a ubuntu box boot up and automatically log a user in on a serial terminal getting to shell. Then the audio device will send a command to run a script. I have the terminal server running by editing  [I]/etc/event.d/ttyS0 and adding:
[/I]# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

and now i get the login prompt when i conncect from another box via minocom.
my question now is how can setup auto login on ttyS0? security isn't a concern on this.
thank-you!!

---

