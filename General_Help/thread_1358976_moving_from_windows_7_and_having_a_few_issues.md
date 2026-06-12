---
title: "moving from windows 7 and having a few issues"
date: 2009-12-19
forum: General Help
---

### Post by Reliam on 2009-12-19
**OS:** Ubuntu 9.10 Minimal Install
**WM:** Openbox
**Graphics:** nVidia 8800 GTS, Dual Monitors, Twinview
**Packages:** openbox obconj openbox-themes menu lxappearance thunar thunar-volman thunar-archive-plugin thunar-thumbnailers nvidia-settings nvidia-glx-185 xcompmgr filezilla vlc eclipse banshee firefox conky tint2 nitrogen feh acroread keepassx gimp g15daemon g15macro ubuntu-restricted-extras miro alsa-utils alsa-base alsamixergui pulseaudio padevchooser paman paprefs pavucontrol pavumeter gstreamer0.10-pulseaudio asoundconf-gtk

[B]
1. Cannot access my mounted FreeNAS cifs share. Have tried[/B]

sudo mount -t cifs //<IP Address>/<Share> /media/NAS -o username=<username>,password=<qapmoc>
sudo mount -t cifs //<IP Address>/<Share> /media/NAS -o username=<username>,password=<qapmoc>,iocharset=utf8,file_mode=0777,dir_mode=0777

The share mounts but when I try to access the directory it says "Permission Denied"
[B]
2. Confused about Openbox Dock, Notifications, and System Tray Setup...[/B]

**A.** What is Openbox Dock exactly... is it suppose to be a system tray... and if so why does it not show up when something is docked in it like Banshee.
**B.** I use Truecrypt when it I finish mounting my drives and exit it leaves the Truecrypt system tray icon in a random place on the desktop I used it on... not going to "Openbox Dock" I have tried changing settings and it doesn't move.
**C.** Is there a simple "system tray" application I can use that will take control of Truecrypt, Banshee, Hamachi etc and show notification?

**3. Hulu desktop seems to only work properly on one monitor when I drag it to the other it complains about the resolution changing and asks to be restarted. It will play but constantly flickering... this happens even if its started on the second monitor.** I will probably have to post this on the hulu boards but figured I will ask while I am here :).

Any help would be appreciated.


**Note:** Already clicked to posted this but I was logged out and I did not see it on the list... So if there is another thread that is the same can a mod delete this one please.

---

