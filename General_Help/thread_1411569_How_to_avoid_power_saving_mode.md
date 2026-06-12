---
title: "How to avoid power saving mode?"
date: 2010-02-20
forum: General Help
---

### Post by laxmi_p on 2010-02-20
Hi All,
I work on Ubuntu 9.04. Our application requirement is NOT to go to power saving mode when application is running. I added ServerFlags section to /etc/X11/xorg.conf
Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
 
This didn't help.
Then I tried following commands
gconftool-2 -s /apps/gnome-power-manager/ac_sleep_display --type=int 0
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
 
I see that it works fine only if I change settings via Settings>ScreenSaver>Power Management in gnome. I wan to do this via script. Can I do this? Which file gets updated when I change display settings via Settings>ScreenSaver>Power Management.
Immediate help would be highly appreciated.
 
Thank You

---

### Post by Pjotr123 on 2010-02-20
Try the policy kit hack described here (step 2):
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-work-we](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-work-we)

---

### Post by laxmi_p on 2010-02-22
> **Pjotr123 said:**
> Try the policy kit hack described here (step 2):
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-work-we](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Hibernate-and-suspend-don-t-work-we)

This didn't work for me. File 
/usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy
 doesn't exist on my machine. 

I'm trying to find out, when I change settings via Settings>Screensaver>Power Management in gnome, which config file am I actually editing? (i.e. where are the settings stored?).

---

### Post by laxmi_p on 2010-02-25
I found that when I change settings via Settings>Screensaver>Power Management in gnome, it edits %gconf.xml file under .gnome/apps/gnome-power-manager/timeout for display and computer sleep changes.

If the above folder doesn't exist we need to create it and then run following commands -

gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false
gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_computer_ac --type=int 0
gconftool-2 -s /apps/gnome-power-manager/timeout/sleep_display_ac --type=int 0

---

