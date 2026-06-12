---
title: "Problem with Simple Backup"
date: 2009-07-03
forum: General Help
---

### Post by biffthemandible on 2009-07-03
When i try to backup my computer using the Simple Backup program it tells me a backup program is running in the background and it gives me an ID number but nothing seems to happen and then the program freezes. What's the problem and how do I fix it? Help very much appreciated.

---

### Post by ajgreeny on 2009-07-03
Have a look in the processes tab of System > Administration > System Monitor to see if there is anything that looks like a backup program already running, but if you find nothing, then I haven't a clue.

---

### Post by biffthemandible on 2009-07-03
These are the only processes running and they are all sleeping. 

bonobo-activation server
compiz
compiz-decorator
compiz.real
dbus-daemon
dbus-launcher
dropbox
firefox
gconfd-2
gconf-helper
gksu
gksu
gnome-keyring-daemon
gnome-panel
gnome-power-manager
gnome-screensaver
gnome-settings-daemon
gnome-system-monitor
gtk-window-decorator
gvsfd
gvsfd-burn
gvsfd-trash
gvfs-fuse-daemon
gvfs-gphoto2-volume-
gvfs-hal-volume-monitor
indicator-applet
mixer_applet2
nautilus
nm-applet
notify-osd
pulseaudio
python
sh
ssh-agent
su-to-root
vino-server
x-session-manager

And when I press 'Backup Now!' it gives me this message:

"A backup run is initiated in the background. The process id is [insert number here]"

Then I go and check the system monitor and the id number given doesn't correspond to any of the processes.

---

### Post by ajgreeny on 2009-07-04
Sorry, but I will have to leave this to others.  I have never used simple-backup, but just rsync or grsync, the second of which I suggest you have a look at.  It does a terrific job of incremental backups of your /home, which is probably the most important part of your install, but it can also backup the filesystem if you want.

---

### Post by johndessuza on 2009-07-04
Hi dear friends,
I just installed sbackup on *Ubuntu* Feisty and when I try to *backup* to my external USB drive, I only get a file called &#8220;ver&#8221; and no other.
I activate the prog and then follow the main window and ask me for the root password. It's solved.

---

