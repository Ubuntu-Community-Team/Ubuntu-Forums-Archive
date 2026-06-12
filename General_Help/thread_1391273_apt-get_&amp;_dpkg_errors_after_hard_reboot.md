---
title: "apt-get &amp; dpkg errors after hard reboot"
date: 2010-01-26
forum: General Help
---

### Post by shoganai on 2010-01-26
Hi all-

I'm running 9.10 on a Dell IM1012-6780BK netbook (very nice and snappy, btw).  I was in the process of installing the ubuntu-restricted packages (apt-get was halfway into setting-up libtwolame0) when the machine locked up and I was forced to do a hard reboot.  Now, at the CLI, I try to remove the corrupted package before re-installing, but I get the following errors: (they seem to be persistent, no matter what I'm trying to install/uninstall via apt-get...

$ sudo apt-get --purge remove ubuntu-restricted-extras

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-restricted-extras is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libmp3lame0 (3.98.2+debian-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmp3lame0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libx264-67 (1:0.svn20090621+git364d7d-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libx264-67 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly-multiverse:
 gstreamer0.10-plugins-ugly-multiverse depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 gstreamer0.10-plugins-ugly-multiverse depends on libx264-67 (>= 1:0.svn20090502); however:
  Package libx264-67 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly-multiverse (--configure):
 dependency problems - leaving unconfigured
Setting up libmp4v2-0 (1:1.6dfsg-0.2ubuntu5) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmp4v2-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of mplayer-nogui:
 mplayer-nogui depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 mplayer-nogui depends on libx264-67 (>= 1:0.svn20090502); however:
  Package libx264-67 is not configured yet.
dpkg: error processing mplayer-nogui (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mplayer:
 mplayer depends on mplayer-nogui; however:
  Package mplayer-nogui is not configured yet.
 mplayer depends on libmp3lame0; however:
  Package libmp3lame0 is not configured yet.
 mplayer depends on libx264-67 (>= 1:0.svn20090502); however:
  Package libx264-67 is not configured yet.
dpkg: error processing mplayer (--configure):
 dependency problems - leaving unNo apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                             configured
dpkg: dependency problems prevent configuration of smplayer:
 smplayer depends on mplayer | mplayer-nogui; however:
  Package mplayer is not configured yet.
  Package mplayer-nogui is not configured yet.
dpkg: error processing smplayer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smplayer-themes:
 smplayer-themes depends on smplayer; however:
  Package smplayer is not configured yet.
dpkg: error processing smplayer-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smplayer-translations:
 smplayer-translations depends on smplayer (>= 0.6.7-1); however:
  Package smplayer is not configured yet.
dpkg: error processing smplayer-translations (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-liberation (1.05.1.20090721-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-liberation (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up ttf-mscorefonts-installer (3.0) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up unrar (1:3.9.3-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing unrar (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libmp3lame0
 libx264-67
 gstreamer0.10-plugins-ugly-multiverse
 libmp4v2-0
 mplayer-nogui
 mplayer
 smplayer
 smplayer-themes
 smplayer-translations
 ttf-liberation
 ttf-mscorefonts-installer
 unrar
E: Sub-process /usr/bin/dpkg returned an error code (1)


This has essentially crippled my ability to install/remove software, so if anyone has any advice, I'd really, truly, absolutely love to hear it, before I go re-installing Karmic (dang, and I just got GNOME configured the way I like too).  Thank you!

---

### Post by BigCityCat on 2010-01-26
my disclaimer....not an expert.

Did you try restarting and booting into recovery mode and using the fix broken packages selection?

---

### Post by shoganai on 2010-01-27
Thanks for the suggestion BigCityCat.  I booted into recovery mode and selected fix broken packages.  It claims to have fixed some pulseaudio issues, but the errors from the OP still persist.

On the bright side, though, is that it actually doesn't appear to affect my ability to install from repos, contrary to what I thought.  So I can either live with it, or re-install karmic, and neither is a very good solution.

---

### Post by BigCityCat on 2010-01-27
Well I'm using Kubuntu so it's hard for me to help you any further. Only suggestion I have is in synaptic click on settings/filters and if you have broken packages it should identify them. That might make it easier to isolate your problem. Also try dpkg rather than purge. I don't really know if that makes a difference. Maybe you will get a response out of this bump.

---

