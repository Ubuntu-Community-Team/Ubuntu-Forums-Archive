---
title: "No more blackberry support?"
date: 2010-06-30
forum: General Help
---

### Post by Dportner on 2010-06-30
iv always had perfect connectivity with my blackberry tour. All i ever had to do was plug it in via usb and presto, there it is... but for some reason this no longer works :S
all the setting on the blackberry itself seem fine for mass storage capability but its just not showing up anymore


*EDIT*

just found out that my VirtualMachine DOES recognize and connect with my blackberry. but why wont ubuntu? O.o

---

### Post by davidmohammed on 2010-06-30
not clear on your setup...

have you got ubuntu installed on PC or as a virtual machine?

what version of ubuntu have you installed?

what has changed since you last connected your blackberry to ubuntu when it was working?

---

### Post by Dportner on 2010-07-06
ubuntu 10.04 is my main setup and i have windows 7 as my virtual machine

pretty sure ever since 10.04 iv had troubles connecting my blackberry

it seems as tho to get my blackberry connected i have to first start up my virtual machine, then turn that off, and then finally ubuntu will recognize that i have my blackberry connected

i know its kindof hard to understand :P

*edit*
i did the lsusb command and my RIM device IS showing up, its just not mounting :/
all the setting on the actuall phone itself are fine (media card support:on  media transfer protocal:on  mass storage mode support:on  auto enable mass storage mode when connected:yes)

sooo im not sure what to do, its just not mounting :/


*another update here*
k so when i do my little trick of powering on the VM, connecting blackberry, disconnecting blackberry, turn off VM to get my blackberry to connect in ubuntu i get this error message:
Cannot connect BLACKBERRY
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

dunno if that helps or just makes you more confused lol

---

### Post by noway2 on 2010-08-05
The thread is a few weeks old, but I did find a solution and am posting it as it may help someone in the future.

This was found on Launchpad indicating that this may be a known bug ([https://answers.launchpad.net/ubuntu/+question/109180](https://answers.launchpad.net/ubuntu/+question/109180)).  The problem appears to be a conflict with the barry package bcharge program where the bcharge application blocks the USB traffic. As a work around, simply rename /usr/sbin/bcharge to something like /usr/sbin/bcharge.bak.  This will restore your mass storage connection.

---

