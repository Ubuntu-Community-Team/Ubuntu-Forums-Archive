---
title: "Problem connecting iPhone to Lucid"
date: 2011-10-31
forum: General Help
---

### Post by InTheNameOfDelicious on 2011-10-31
Hello all,

I have a problem connecting my iPhone 3GS running os 4.3.5 to my computer running Lucid. I'm sure the problem is with the computer and not the phone. The phone connects fine to my friends computer, with a clean installation of Lucid.

A while ago I was messing with jailbreaking and per some tutorial suggestion I switched from the Gnome native support packages to those in the pmcenery ppa [https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)
Then it worked fine... But after I undid the jailbreak and installed 4.3.5 on the phone, my ubuntu stopped recognizing it. It doesn't mount.

Since my friend's computer mounts the phone fine, I decided to compare the list of packages we have installed. I found that he has libgvfscommon0 and I don't, so I tried to install it but the installation wants to remove a ton of other stuff. Here's the list:

[FONT="Courier New"][SIZE="1"]brasero evolution evolution-couchdb evolution-exchange evolution-indicator evolution-plugins f-spot gbrainy gdm gdm-guest-session ghex gnome-about gnome-applets gnome-do gnome-do-docklets gnome-do-plugins gnome-mag gnome-orca gnome-panel gnome-power-manager gnome-session gnome-utils gvfs gvfs-backends gvfs-bin gvfs-fuse indicator-applet indicator-applet-session indicator-me libbonoboui2-0 libgail-gnome-module libgnome-pilot2 libgnome2-0 libgnome2-perl libgnome2.24-cil libgnomepanel2.24-cil libgnomeui-0 liblpint-bonobo0 libpanel-applet2-0 mousetweaks nautilus nautilus-share python-gnome2 python-gnomeapplet python-pyatspi rhythmbox rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone-music-store screenlets soundconverter system-config-printer-gnome tomboy tsclient ubuntu-desktop usb-creator-gtk vinagre[/SIZE][/FONT]

I couldn't uninstall the packages from the pmcenery ppa and install back those from the official ubuntu repo because that also wants to remove a list of packages similar to the above.

Does anybody know how to fix this issue? Thanks

---

### Post by InTheNameOfDelicious on 2011-11-01
I resolved the iPhone connection issue with the suggestion from [_this thread_]("http://ubuntuforums.org/showthread.php?t=1861617").

I'm still curious though as to why would aptitude want to remove that whole list of packages when I try to install libgvfscommon0?

---

