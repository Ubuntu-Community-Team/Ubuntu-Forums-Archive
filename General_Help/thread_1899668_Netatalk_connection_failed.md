---
title: "Netatalk connection failed"
date: 2011-12-24
forum: General Help
---

### Post by k-laminero on 2011-12-24
Hi!

I am trying to setup an external hdd connected via usb to my ubuntu desktop to be accessible to a mac laptop (running 10.5.8)

I dont know anything about mac but I will try to be as descriptive as possible.

[Config]
_Desktop computer_ running ubuntu 11.10 (64 bit)
The external computer is a WD HDD connected via usb.
The desktop computer is connected via wireless to the internet router
I installed netatalk following (more or less) this guide [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/]("http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/")
minus the time machine part.
My AppleVolumes.default looks like this
# The line below sets some DEFAULT, starting with Netatalk 2.1.
:DEFAULT: options:upriv,usedots
/media/Elements "Elements" allow:USERNAME cnidscheme:dbd
And my afpd.conf:
# default:
# - -transall -uamlist uams_dhx2.so -nosavepassword
- -transall -uamlist uams_dhx.so -nosavepassword -advertise_ssh
Now even though that seems like a minor detail, I should mention that when i edit these files from the terminal with gedit, a gtk warning shows up: (gedit:3467): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
But the files seem to be properly saved...


_Mac laptop:_
Running 10.5.8, connected to the same internet wireless router (the network is protected but i do not have access to the router)

[Behavior]
On the mac, when I open Finder, I see on the left side an icon with my ubuntu comp's name under "SHARED" but there is no eject icon at the right of it.
I click on "Connect As". By default, the Name is filled with the profile name of the person owning the mac. I replace it with the USERNAME i set in AppleVolumes.default and i get a connection failed window: "There was an error connecting to the server. Check the server name or IP address and try again."

[Noteworthy]
The behavior does not change if I enter a bogus username. 
I do not have a password set yet.
Not interested in setting up time machine, just file access.
The folder is shared through the regular file explorer. Should i disable that?
I installed samba. Could that be interfering?

[Questions]
Any idea whats causing this?
In applevolumes.default, should the username be surrounded by quotes? 

Thanks guys

---

### Post by k-laminero on 2011-12-28
up?

---

### Post by k-laminero on 2012-01-02
up? Nobody has insight on the issue??
:confused::confused::confused:

---

### Post by k-laminero on 2012-01-03
up...

---

### Post by tabasko on 2012-01-12
Howdy mate :KS,

Is the username you have in applevolumes.default existing at the ubuntu-box as real user? I first tried to put in afp volume-config my Mac username and thats not working, you should use that user which has access on share on local ubuntu-box. And when you connect from finder, use that ubuntu's username and its password to log in to share.

Samba doesn't interfer to afp/netatalks behaviour. Also you should check that you have port open for netatalk service on ubuntu.

I hope you get it working. But still, I don't see reason to use afp until youre going to use your ubuntu-box as time machine :) Samba does file sharing job too. Oh yeah, you can choose better icon for your share, samba shares show up with bsod-icons in finder :)

---

