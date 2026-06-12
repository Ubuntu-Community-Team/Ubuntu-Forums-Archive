---
title: "Trouble in Synaptic and terminal after system lock-up.."
date: 2010-01-30
forum: General Help
---

### Post by wanderingarticfox on 2010-01-30
I'm reposting here; I posted in Install and Upgrades originally but have had no replies or help. My system locked-up/froze during the use of Update manager and now I can not figure out what is going on. I'm new and trying to learn about the terminal command stuff but I really do not know what to do at this point. Below is some of what I posted in the other thread:

I was running Update manager and my old system pull a 'freeze/lockup' before things were completed so I have tried using apt-get ; I first updated then upgraded and get the same issue as in Update mgr with 2 small packages, 1 Rythmbox and 1 software center


I ran sudo dpkg --configure -a   in the terminal, and this is what I got back: 

Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-esound-compat (--configure):
dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Errors were encountered while processing:
rhythmbox
pulseaudio
pulseaudio-module-bluetooth

Please help. I'm trying to learn here.

I'm reading at this info and have tried installing the rhythmbox and pulse audio stuff, even tried uninstalling and reinstalling all of rhythmbox. I think something is 'hung' up or broken from when my system locked-up/froze during the use of update manager

33333333333-desktop:~$ sudo dpkg --configure -a
[sudo] password for 33333:
dpkg: error processing rhythmbox (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of rhythmbox-dbg:
rhythmbox-dbg depends on rhythmbox (= 0.12.5-0ubuntu5.2); however:
Version of rhythmbox on system is 0.12.5-0ubuntu5.1.
dpkg: error processing rhythmbox-dbg (--configure):
dependency problems - leaving unconfigured

Package pulseaudio-module-raop is not configured yet.
dpkg: error processing pulseaudio-module-raop-dbg (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-esound-compat:
pulseaudio-esound-compat depends on pulseaudio (= 1:0.9.19-0ubuntu4.1); however:
Package pulseaudio is not configured yet.
dpkg: error processing pulseaudio-esound-compat (--configure):
dependency problems - leaving unconfigured

I imagine I have overlooked something but being new to terminal commands that should not be surprising Help if you can. I am trying to learn how to read and understand this out-put.

---

### Post by blueshiftoverwatch on 2010-01-30
Maybe you should just go to Synaptic (not Update Manager) and uninstall and than reinstall the packages listed before trying to update them again.

---

### Post by wanderingarticfox on 2010-01-31
Well I've been trying to do just that but it is not working; I am to a point where I need to disable 'third party repositories' but I get lost in all the available documentation trying to figure out how to do that. If some one could let me know how to disable the third party repositories in the 'terminal' That would be a big help.
I would think that using 'sudo' in the terminal would be more effective than using the GUI in Synaptic, am I correct?

---

