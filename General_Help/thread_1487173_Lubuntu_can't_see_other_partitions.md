---
title: "Lubuntu can't see other partitions"
date: 2010-05-18
forum: General Help
---

### Post by egeezer on 2010-05-18
I have Lubuntu 10.04 installed and working, but none of the other partitions on the drive are listed in Nautilus and although a USB drrive will flash as if mounting, it does not appear anywhere.
Any thoughts?

---

### Post by 2hot6ft2 on 2010-05-18
If they are formatted to NTFS go to
Menu > Preferences > NTFS Configuration Tool
and set it up.
If not then this may help
Open a terminal
Menu > Accessories > Terminal
and run
```
sudo apt-get install systemsettings
```
then
1. Go to Menu --> Preferences --> System Settings
2. A Systems Settings Window will pop-up
3. On the Systems Settings Window click on the 'Advanced' Tab (the other one is 'General')
4. On the section 'Advance User Settings' look for 'Removable Devices' and click on it
5. This will take you to Removable Devices - System Settings Window.
6. Click 'Enable automatic mounting of removable media' and Apply
:popcorn:

---

### Post by egeezer on 2010-05-18
Thank you for those outstanding directions!  Sadly, they just didn't work.  Still no recognition of other partitions, USB stick flashes but does not show on desktop.  I'm thinking Lubuntu is NOTHING like Ubuntu - my Ubuntu 10.04 installed flawlessly and works like a charm - my favorite distro ever!

---

### Post by egeezer on 2010-05-18
To clarify: on the desktop machine where I installed Lubuntu I'm also running SliTaz and a small minimal-install homemade version of Ubuntu 9.10 I call Mouse.  Those two can see and access Lubuntu and each other, but Lubuntu thinks it's all alone on the drive - probably the same reason it can't see the USB.
I'm thoroughly puzzled!

---

