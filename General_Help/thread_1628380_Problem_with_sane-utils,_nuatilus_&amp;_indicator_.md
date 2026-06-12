---
title: "Problem with sane-utils, nuatilus &amp; indicator applet"
date: 2010-11-22
forum: General Help
---

### Post by com_kieffer on 2010-11-22
Hello, I'm having a couple of issues that suddenly started yesterday :

I - Update Manager

When i run the update manager and click on the "check" button to check for updates a dialog pops up :

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

Running "sudo apt-get update" from the terminal works fine, but running "sudo apt-get upgrade" returns :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  binfmt-support cpp g++ gcc ghostscript ghostscript-x gir1.0-glib-2.0 gstreamer0.10-plugins-good libavcodec52
  libavformat52 libavutil50 libcanberra-gtk0 libgdk-pixbuf2.0-0 libgexiv2-0 libgphoto2-2 libnice0 libpcsclite1
  libpostproc51 libsane libswscale0 linux-generic linux-headers-generic linux-image-generic man-db perl
  perl-base perl-modules python-apt python-uno shotwell simple-scan speech-dispatcher tcl telepathy-gabble
  uno-libs3 ure vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse x11-utils xserver-xorg xserver-xorg-core
  xserver-xorg-video-nouveau
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up sane-utils (1.0.22~git1.0.21-157-g126c70d-1) ...
adduser: The group `scanner' does not exist.
dpkg: error processing sane-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 sane-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)


II - nautilus

Around the same time i started having issues with sane-utils nautilus started behaving strangely : On startup a bunch of instances of nautilus would try to launch and by a bunch i mean hundreds but none would actually get to open a window because new instances just keep on appearing. instead they would fill up the lower gnome panel bar. Opening a terminal and running "killall nautilus" gets rid of them. Somehow when i started my computer after coming home from uni no nautilus spam altough it had happened every time I started the computer today. Now when i try and launch nautilus from the terminal by running "nautilus" a message appears on the terminal : 

(nautilus:11757): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:11757): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

III - Indicator applet (sound)

When I want to change the volume I click on the speaker icon and a small menu appears underneath it. So far so good, but when i click on the slider to adjust the sound the applet crashes and a dialog appears :

"Indicator Applet" has quit unexpectedly

with the option to reload or not the applet. Reloading does not solve the problem, trying to change the volume from the applet will make it crash again.

And that's all my problems, any help would be greatly appreciated. 

The only "bad" thing I've done that maybe could have something to do with the problems is adding the debian experimental repository to download arduino 0021 as the official ubuntu repository only has 0018 but 0021 is an official release by the arduino team for the arduino uno board so i don't believe iti is the cause of the problem.

Any insight into my problems would be great, thank you.

---

