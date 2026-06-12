---
title: "screensaver is playing while viewing a video in vlc"
date: 2009-11-12
forum: General Help
---

### Post by prakreet on 2009-11-12
I am using ubuntu 9.10 Karmic Koala. The screensaver is set to play when computer is idle for 5 min.. But when i am viewing a movie in vlc (v1.0.3) the screensaver starts playing.. is it a bug... why does't it recognise that vlc is playing a video...

---

### Post by 0cton on 2009-11-12
I used to have the same problem when it's not full screen but with totem.
It is technically not a bug cause there is like "no" activity from your part, but at the same time it is not idle.

---

### Post by ddarsow on 2009-11-12
> **prakreet said:**
> I am using ubuntu 9.10 Karmic Koala. The screensaver is set to play when computer is idle for 5 min.. But when i am viewing a movie in vlc (v1.0.3) the screensaver starts playing.. is it a bug... why does't it recognise that vlc is playing a video...

install caffeine, it keeps that from happening and is even configurable to auto start when you launch certain apps.

---

### Post by jtniehof on 2009-11-12
In VLC:
Tools->Preferences
Bottom left, "Show settings", pick "All"
Click on "Video." Should bring up "General Video Settings"
About the tenth item down is "Disable Screensaver." Make sure this is checked.

---

### Post by mc4man on 2009-11-12
see here
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/428884)

best fix - turn off screensaver

---

### Post by ddarsow on 2009-11-12
> **jtniehof said:**
> In VLC:
Tools->Preferences
Bottom left, "Show settings", pick "All"
Click on "Video." Should bring up "General Video Settings"
About the tenth item down is "Disable Screensaver." Make sure this is checked.

even with the screensaver turned off, some monitors will shut down after a period of inactivity to conserve power. Caffeine is a very low resource app which only runs when needed and covers this as well. ;)

---

### Post by prakreet on 2009-11-12
The disable screensaver option is enabled.. as mc4man has stated this is a bug..

vlc is the most popular and used software oss software out there. bugs concerning such an app should be a high priority..

---

### Post by falconindy on 2009-11-12
There's 2 fixes available, both of them available in the link posted earlier:

1) Install the gnome-screensaver package from the motumedia PPA.
2) Get the diff package, download the gnome-screensaver source using apt-get, and patch/build it yourself.

I've used both routes and they work. No need to ditch VLC.

---

