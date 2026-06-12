---
title: "No volume OSD, hotkeys doesnt control software Mixer"
date: 2010-02-12
forum: General Help
---

### Post by un234567 on 2010-02-12
hello there, this is my first post in this forum, ill be direct to the point.

last week I upgraded from intrepid to jaunty knowing that I can downgrade xserver to 1.52 in order to run the fglrx drivers for my ati x1400. Everything went well except for 1 thing. [COLOR="Red"]The volume OSD disappeared and the volume hotkeys no more control the software mixer.[/COLOR] I am using OSS v4 and during the downgrade process I downgraded gnome-session to 2.24 and gnome-power-manager to 2.24.

I went to keyboard shortcuts and made sure the keys are set up correctly:
XF86AudioRaiseVolume
XF86AudioLowerVolume
XF86AudioMute

I think the problem might be caused by the gnome-settings-daemon as I found the following gconf-editor keys empty:

/apps/gnome-volume-control/active-element
/desktop/gnome/sound/default_mixer_device

I tried to fill them up but no avail.

I appreciate any help

Laptop Specifications:

Thinkpad Z61m
Intel Core 2 DUO T7200
ATI Radeon X1400
Intel Hd audio AD1981 running well on OSSv4  
3 GB Ram

---

### Post by farso23 on 2010-02-13
what exactly did u put in the following:

/apps/gnome-volume-control/active-element
/desktop/gnome/sound/default_mixer_device

---

### Post by un234567 on 2010-02-14
Well i tried to put /dev/mixer and /dev/mixer0 cuz i hv mixer0 in the /dev directory which links directly to /dev/oss/oss_hdaudio0/mix0. I tried to put the link of mixer0 there too. It is as if the settings daemon affects nothing.

I really need help getting this working. Also I have another issue, when I plug or unplug the AC adapter the screen goes blank. I have to close the lid and open it again to make the screen work. Sometimes it locks down and nothing can make the screen work other than a restart.

waiting for your replies

---

