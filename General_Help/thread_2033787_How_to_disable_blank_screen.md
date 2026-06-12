---
title: "How to disable blank screen?"
date: 2012-07-26
forum: General Help
---

### Post by michaelbr on 2012-07-26
Greetings all:
I have the following environment:
- Ubuntu 12.04 with Unity
I've installed XScreenSaver, then removed it using Synaptic Manager, whenever the computer is idle for 10min, the screen went blank, after searching web, I took the following steps:
- System Settings > Power > Suspend when inactive for set to Don't suspend
- System Settings > Brightness and Lock > Turn screen off when inactive for set to Never
but still it showed blank screen after 10min
- in terminal, issued the following command ```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```, then issued ```
gsettings get org.gnome.desktop.screensaver idle-activation-enabled
``` and it returned false, but still I got blank screen after 10min, is there anywhere else that I should check/set in order to disable the blank screen?

Found solution on this site [http://askubuntu.com/questions/140680/vlc-does-not-inhibit-screen-blanking](http://askubuntu.com/questions/140680/vlc-does-not-inhibit-screen-blanking)
The only way I managed to disable the screen blanking is using the command line utility xset: xset -dpms and xset s off (it's possible only one of these is necessary).

---

