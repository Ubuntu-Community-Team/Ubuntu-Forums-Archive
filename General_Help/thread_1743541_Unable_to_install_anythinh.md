---
title: "Unable to install anythinh"
date: 2011-04-29
forum: General Help
---

### Post by ambdeep on 2011-04-29
Im getting the "errors were encountered while processing" error every time i try and install anything. Please help.

```
(Reading database ... 189666 files and directories currently installed.)
Removing bluetooth ...
ambdeep@Amber:~$ sudo apt-get check
sudo: unable to resolve host Amber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 bluez-utils : Depends: bluetooth but it is not installed
E: Unmet dependencies. Try using -f.
ambdeep@Amber:~$ sudo apt-get install -f
sudo: unable to resolve host Amber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  bluetooth
The following NEW packages will be installed:
  bluetooth
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/12.6 kB of archives.
After this operation, 73.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package bluetooth.
(Reading database ... 189660 files and directories currently installed.)
Unpacking bluetooth (from .../bluetooth_4.91-0ubuntu1_all.deb) ...
Setting up bluez (4.91-0ubuntu1) ...
groupadd: cannot lock /etc/gshadow; try again later.
addgroup: `/usr/sbin/groupadd -g 134 bluetooth' returned error code 10. Exiting.
dpkg: error processing bluez (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bluez-alsa:
 bluez-alsa depends on bluez; however:
  Package bluez is not configured yet.
dpkg: error processing bluez-alsa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-gstreamer:
 bluez-gstreamer depends on bluez; however:
  Package bluez is not configured yet.
dpkg: error processing bluez-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluetooth:
 bluetooth depends on bluez; however:
  Package bluez is not configured yet.
dpkg: error processing bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-utils:
 bluez-utils depends on bluetooth; however:
  Package bluetooth is not configured yet.
dpkg: error processing bluez-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuratiNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                       No apport report written because the error message indicates its a followup error from a previous failure.
                 No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         on of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez
 bluez-alsa
 bluez-gstreamer
 bluetooth
 bluez-utils
 gnome-bluetooth
 gnome-user-share
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by KegHead on 2011-04-29
Hi!

Try in terminal;

sudo apt-get update

sudo apt-get update -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

KegHead

---

### Post by ambdeep on 2011-04-29
Getting the same error after "sudo apt-get dist-upgrade -f"

---

### Post by KegHead on 2011-04-29
Hi!

Did the first 2 commands work?

also run;

sudo apt-get install linux-image -f
[COLOR="Red"]restart.[/COLOR]

The files are asking you to set up blutooth..have you?

KegHead

---

### Post by ambdeep on 2011-04-29
the first 2 commands ran. the last 2 commands give the same error. as for my bluetooth, it seems to be functional. i think i should also mention that this started to happen after my update manager crashed in the middle of a partial update.


Ive also rebooted, but still have the same problem.

---

### Post by KegHead on 2011-04-29
Hi!

I see.

Is there chance you could load a fresh copy of 11.04 on a usb stick and reinstall?

[COLOR="Red"]If you can, back up your files.[/COLOR]

KegHead

---

### Post by ambdeep on 2011-04-29
> **KegHead said:**
> Hi!

I see.

Is there chance you could load a fresh copy of 11.04 on a usb stick and reinstall?

[COLOR="Red"]If you can, back up your files.[/COLOR]

KegHead
I would love to avoid that. I havent needed to do that in 2 years and im sure linux has a more elegant solution than formatting the partition.

---

### Post by KegHead on 2011-04-29
Hi!

With a broken download it would be very difficult.

You could look here, but you'd need the names of the files needed.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

IMHO The reinstall would be faster.

KegHead

---

### Post by ambdeep on 2011-04-30
*bump*
HELP!!!!

---

### Post by HiImTye on 2011-04-30
it says:
```
groupadd: cannot lock /etc/gshadow; try again later.
```try
```
sudo rm /etc/gshadow.lock
```should let you install again

please mark as solved if this fixes it or else comment back and Ill see what else I can get you to try

---

### Post by ambdeep on 2011-04-30
> **HiImTye said:**
> it says:
```
groupadd: cannot lock /etc/gshadow; try again later.
```try
```
sudo rm /etc/gshadow.lock
```should let you install again

please mark as solved if this fixes it or else comment back and Ill see what else I can get you to try
It worked!!!!
THANKS A LOT!!!

---

### Post by HiImTye on 2011-04-30
no problemo

---

