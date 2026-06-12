---
title: "Editing Startup Applications"
date: 2010-10-16
forum: General Help
---

### Post by SPMcKinney on 2010-10-16
First of all I'm not sure if this is the right page to put this but o well, on my Ubuntu 10.04 I want to stop some programs from Startup Applications to free up some of my virtual memory and ram, I want to know what programs I don't need running


Here's a list of the Startup Applications

Bluetooth Manager
Certificate and Key Storage
Check for new hardware drivers
Disk Notifications
Evolution Alarm Notifier
GNOME Login Sound
Network Manager
Personal File Sharing
Power Manager
Print Queue Applet
PulseAudio Sound System
Remote Desktop
Secret Storage Service
SSH Key Agent
Ubuntu One
Update Notifier
User folders update
Visual Assistance

---

### Post by Isyaltut on 2010-10-16
> **SPMcKinney said:**
> First of all I'm not sure if this is the right page to put this but o well, on my Ubuntu 10.04 I want to stop some programs from Startup Applications to free up some of my virtual memory and ram, I want to know what programs I don't need running


Here's a list of the Startup Applications

Bluetooth Manager
Certificate and Key Storage
Check for new hardware drivers
Disk Notifications
Evolution Alarm Notifier
GNOME Login Sound
Network Manager
Personal File Sharing
Power Manager
Print Queue Applet
PulseAudio Sound System
Remote Desktop
Secret Storage Service
SSH Key Agent
Ubuntu One
Update Notifier
User folders update
Visual Assistance

I suppose it all depends on your intention which program or function to use. For example I don't use: 

Bluetooth Manager: don't have any bluetooth device to connect
Check for new hardware drivers: already installed at first run
Evolution Alarm Notifier: don't use evolution, uninstall it, use thunderbird instead
Remote Desktop: not sure what it does
Ubuntu One: don't use Ubuntu one
Update Notifier: I prefer to update manually.

I haven't encounter any problem with those above program disable btw

---

### Post by VMC on 2010-10-16
> **SPMcKinney said:**
> First of all I'm not sure if this is the right page to put this but o well, on my Ubuntu 10.04 I want to stop some programs from Startup Applications to free up some of my virtual memory and ram, I want to know what programs I don't need running


Here's a list of the Startup Applications

Bluetooth Manager
Certificate and Key Storage
Check for new hardware drivers
Disk Notifications
Evolution Alarm Notifier
GNOME Login Sound
Network Manager
Personal File Sharing
Power Manager
Print Queue Applet
PulseAudio Sound System
Remote Desktop
Secret Storage Service
SSH Key Agent
Ubuntu One
Update Notifier
User folders update
Visual Assistance

To get you started, go to "System > Preferences > Startup Applications", then untick what you don't want started.

---

### Post by Aspiring_Failure on 2010-10-16
I believe you don't really *need* anything turned on. You're not turning off services, or actual components of the OS, like you'd be with the Windows Services, but just which applications start up whenever you boot up the OS.

Turn it all off, if you don't use any of it. (Except maybe the Gnome keyring applications, I think those might be important for security)

---

### Post by SPMcKinney on 2010-10-16
Ok all I do is go on the Internet thats it

---

### Post by owiknowi on 2010-11-29
I've also turned off, deleted the formentioned "services" and even de-installed some of the software I don't need.

Still I've found errors in home/username/.xsession-errors about some of the "services" I've turned of.

Where can I find (system) files where I can choose and edit my system so it works like I want it to?

BTW: I also see that there are several applications creating log files (brasero, furiuos, etc) whitch I can only empty manualy.
Is there a solution for this (bleachbit won't do to the trick).

---

