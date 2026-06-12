---
title: "Synaptic Package Manger Issue"
date: 2010-07-29
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2010-07-29
Hi,

I am suddenly having problems with synaptic package manager. I go to change the proxy to my uni proxy (under settings>preferences>network) and when I click okay/apply it freezes. I've restarted and tried other things and it doesnt work.

I removed the following packages yesterday (not sure if any are relevant):
Completely removed the following packages:
avant-window-navigator
avant-window-navigator-data
bygfoot
festival

Removed the following packages:
aisleriot
awn-applets-c-core
awn-applets-python-core
awn-settings
bogofilter
bogofilter-bdb
bogofilter-common
brltty
brltty-x11
festlex-cmu
festlex-poslex
festvox-kallpc16k
gnome-orca
libawn1
libbrlapi0.5
liblouis-data
liblouis0
openoffice.org-emailmerge
pidgin-musictracker
python-awn
python-awn-extras
python-brlapi
python-louis
python-speechd
speech-dispatcher
transmission-common
vinagre
vino

Reinstalled the following packages:
plymouth-theme-ubuntu-logo (0.8.2-2ubuntu2)


I also used Bootup manager to speed up my boot, but I have enabled any network related services that I can find, to no end.

Any help/advice would be greatly appreciated.

---

### Post by pastalavista on 2010-07-29
I believe uninstalling vinagre and/or vino might have caused your network problems as they are the only network-related packages in your list.

---

### Post by Dalek Draco ON LINUX on 2010-07-29
I drew the same conclusion and I was about to reinstall them when i got home, and I found that the problem had fixed itself :S. Hopefully it'll work tomorrow when I try to suck uni's bandwith :P.

---

