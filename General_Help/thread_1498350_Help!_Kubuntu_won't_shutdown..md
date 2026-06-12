---
title: "Help! Kubuntu won't shutdown."
date: 2010-05-31
forum: General Help
---

### Post by weedwacker on 2010-05-31
Help! Kubuntu won't shutdown.

Tried system upgrade to Kubuntu 10.04 and a fresh install of same and in either
case I cannot shutdown. With Kubuntu 9.10 this was not a problem.

What I get when I click shutdown is a dark screen with the following:

Ubuntu 10.04 LTS kubuntu tty1
kubuntu login: acpid: exiting
init:tty5 main process (852)killed by TERM Signal
init:tty2 main process (857)killed by TERM Signal
init:tty3 main process (850)killed by TERM Signal
init:tty6 main process (860)killed by TERM Signal
init:tty1 main process (998)killed by TERM Signal
init: usplash main process (1679) terminated with status2

Then I get a flashing cursor and the system hangs.

I can do a CTRL+ALT+DELETE that just results in a reboot.

I also experienced a problem with my login which when I installed the system I
for automatic login but now I had to login manually.

I went to System Settings>Advanced>Login Manager to correct this and I found a tab named
"Shutdown" and there I saw that HALT pointed to the /sbin/halt directory.

I checked in root /sbin and found that "halt" is a shortcut and in its Properties
it tells me that "halt" is a shared library that points to...(wait for it!)
"REBOOT"

The "halt that is necessary to shutdown the system is not in /sbin.

As a matter of fact the "Poweroff" shortcut also points to "REBOOT"

I tried a change of the "halt" shortcut to have it point to "shutdown" which is in
/sbin, but that did not result in a shutdown.

Does anyone know how I can resolve this?

---

