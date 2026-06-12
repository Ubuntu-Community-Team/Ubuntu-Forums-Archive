---
title: "Problem with Banshee (Natty)"
date: 2011-04-29
forum: General Help
---

### Post by Inkeed on 2011-04-29
Hi,

Last night I sucessfully installed the update for Ubuntu and all goes pretty well, except one thing : The music.

Firsteval I imported my library from Rythmbox, but when I clicked on a song, there was nothing. During the installation "bluez" failed to install so I tried again :

> Setting up bluez (4.91-0ubuntu1) ...
groupadd: cannot lock /etc/gshadow; try again later.
addgroup: `/usr/sbin/groupadd -g 126 bluetooth' returned error code 10. Exiting.
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
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
dpkg: error processing gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-share:
 gnome-user-share depends on gnome-bluetooth; however:
  Package gnome-bluetooth is not configured yet.
dpkg: error processing gnome-user-share (--configure):
 dependency problems - leaving uncoNo apport report written because the error message indicates its a followup error from a previous failure.
                                                             No apport report written because the error message indicates its a followup error from a previous failure.
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   nfigured
Setting up xfs (1:1.0.8-6) ...
groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 126 debian-xfs' returned error code 10. Exiting.
dpkg: error processing xfs (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 bluez
 bluez-alsa
 bluez-gstreamer
 gnome-bluetooth
 gnome-user-share
 xfs
E: Sub-process /usr/bin/dpkg returned an error code (1)

Somebody knows the magic answer?

Thank you!

Inkeed

---

