---
title: "lubuntu, xubuntu, ubuntu - installing them all ?"
date: 2010-09-21
forum: General Help
---

### Post by petrasflorin on 2010-09-21
OK. I know that you can install xubuntu and lubuntu from ubuntu terminal with just removing ubuntu && sudo apt-get install xubuntu-desktop or lubuntu-desktop.

My question is: can you reverse-engineer that ? i.e installing fresh lubuntu then deciding you want the ubuntu and doing install ubuntu-desktop ? if so, question:

I found the command for removing ubuntu on the net ( [http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce) ) however I have no idea what's the command for removing lubuntu and installing ubuntu ( I mean how do I know the names of all those packages ).

one more question: is there any difference (i.e size wise and performance wise - between installing a fresh lubuntu or a lubuntu installed from the ubuntu environment ? I mean... theoretically...).

Thanks in advance,
shortcut addict.

---

### Post by nothingspecial on 2010-09-22
apt-cache lists the dependencies of lubuntu-desktop as so

```
Dependencies: 
0.13 - abiword (0 (null)) alsa-base (0 (null)) alsa-utils (0 (null)) anacron (0 (null)) aqualung (0 (null)) cheese (0 (null)) chromium-browser (0 (null)) cron (0 (null)) cups-driver-gutenprint (0 (null)) dbus-x11 (0 (null)) desktop-file-utils (0 (null)) epdfview (0 (null)) galculator (0 (null)) gdebi (0 (null)) gksu (0 (null)) gnome-bluetooth (0 (null)) gnome-disk-utility (0 (null)) gnome-mplayer (0 (null)) gnome-power-manager (0 (null)) gnome-system-tools (0 (null)) gnumeric (0 (null)) gpicview (0 (null)) hardinfo (0 (null)) jockey-gtk (0 (null)) language-selector (0 (null)) leafpad (0 (null)) logrotate (0 (null)) lubuntu-artwork (0 (null)) lubuntu-default-settings (0 (null)) lubuntu-plymouth-theme (0 (null)) lxappearance (0 (null)) lxdm (0 (null)) lxinput (0 (null)) lxlauncher (0 (null)) lxpanel (0 (null)) lxrandr (0 (null)) lxsession (0 (null)) lxsession-edit (0 (null)) lxshortcut (0 (null)) lxterminal (0 (null)) mtpaint (0 (null)) network-manager-gnome (0 (null)) ntp (0 (null)) obconf (0 (null)) openbox (0 (null)) osmo (0 (null)) parcellite (0 (null)) pcmanfm (0 (null)) pidgin (0 (null)) pm-utils (0 (null)) pm-utils-powersave-policy (0 (null)) policykit-desktop-privileges (0 (null)) ppp (0 (null)) pyneighborhood (0 (null)) scrot (0 (null)) simple-scan (0 (null)) software-properties-gtk (0 (null)) sylpheed (0 (null)) sylpheed-i18n (0 (null)) synaptic (0 (null)) system-config-printer-gnome (0 (null)) transmission (0 (null)) ttf-liberation (0 (null)) ttf-unfonts-core (0 (null)) ttf-wqy-microhei (0 (null)) unzip (0 (null)) wireless-tools (0 (null)) wpasupplicant (0 (null)) wvdial (0 (null)) x11-utils (0 (null)) xarchiver (0 (null)) xchat (0 (null)) xdg-user-dirs (0 (null)) xdg-utils (0 (null)) xfburn (0 (null)) xfce4-taskmanager (0 (null)) xorg (0 (null)) xscreensaver (0 (null)) xserver-xorg-input-all (0 (null)) zip (0 (null)) powernowd (0 (null)) xserver-xorg-input-evtouch (0 (null))
```

---

### Post by petrasflorin on 2010-09-22
apt-cache showpkg lubuntu-desktop ?

-those ((null)) get me confused.

---

