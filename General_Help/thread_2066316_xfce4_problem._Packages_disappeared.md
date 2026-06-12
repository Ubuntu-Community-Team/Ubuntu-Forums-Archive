---
title: "xfce4 problem. Packages disappeared?"
date: 2012-10-04
forum: General Help
---

### Post by raspatan on 2012-10-04
Hello!

First, thanks for reading this. 
I installed Ubuntu several months ago and have been learing how to use it and etc. I liked a lot, but it went a bit slow in my computer, so I decided to install xcfe, which in some forums people said it was faster. After reading a lot, I installed it from the terminal with this command:

```
*sudo apt-get install xubuntu-desktop*
```I did this like 3 weeks ago. I did not delete gnome since I read that it was better to try it first and that also it may be dangerous. 
Well, everything was fine until today. When I turned on the computer and logged into xfce session, the following message appeared:

unable to launch "startxfce4" X session --- "*startxfce4*" *not found*; falling back to default session. 

Then a black window. I managed to get out of the session and then run the gnome one. I read about this problem and i installed the xfce4-utils, which apparently disappeared.
Then I entered into the xfce session, but the desktop was gray and without icons. In the configuration tools of xfce there was not desktop element! I read again and installed the xfdesktop package from the terminal. Now the element was there and i could configure it. The settings were like I had them before: same wallpaper, same icons position, etc. Now I'm stuck in the notification area. I can't get back the volume icon, the clock and date icon, etc. 
Well, my main question is why did this happened, how to avoid it in the future and what else do I need to restore everything back. How can I see which xcfe packages do i have and have not?

As some useful information, yesterday I was trying to configure the VPN network for my campus wifi. Cisco didn't work, so I installed openconnect. To run this program I had to install network-manager-gnome. I did that and then I could connect to wifi. All fine. Later, i turned off the computer, went back to my place and turned on again, xcfe worked fine and I connected to internet but using my house wifi, so no VPN needed. 

Today in the morning I came to my campus, where I need the VPN stuff, and the startxfce4 problem appeared. I mention this because maybe that gnome package that I installed could cause the problem, as this person suggest: [http://crunchbanglinux.org/forums/topic/10017/solved-network-and-update-notification-icons-missing-in-xfce4panel/](http://crunchbanglinux.org/forums/topic/10017/solved-network-and-update-notification-icons-missing-in-xfce4panel/)

That's it. I won't do anything else, waiting for a reply.

Thank you!!

---

### Post by raspatan on 2012-10-04
I also lost the notes aplication I had. I can't find my notes! Apparently it is the xcfe4-notes plugin.

---

### Post by raspatan on 2012-10-04
Oh my god! I just check the ubuntu software centre and there it is!
Apparently I uninstalled yesterday all xcfe4 stuff!!! 
Could this have happened when i decided to uninstall gnumeric? 

Chek the log of the software center! 

```

Start-Date: 2012-10-01  20:52:22
Commandline: aptdaemon role='role-upgrade-system' sender=':1.70'
Upgrade: thunderbird-globalmenu:i386 (15.0+build1-0ubuntu0.12.04.1, 15.0.1+build1-0ubuntu0.12.04.1), unity-2d:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), unity-2d-panel:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), gvfs-fuse:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), python-software-properties:i386 (0.82.7.2, 0.82.7.3), cheese:i386 (3.4.1-0ubuntu2, 3.4.1-0ubuntu2.1), wine1.5:i386 (1.5.13-0ubuntu1, 1.5.14-0ubuntu1), unity-2d-launcher:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), thunderbird:i386 (15.0+build1-0ubuntu0.12.04.1, 15.0.1+build1-0ubuntu0.12.04.1), grub2-common:i386 (1.99-21ubuntu3.1, 1.99-21ubuntu3.4), cheese-common:i386 (3.4.1-0ubuntu2, 3.4.1-0ubuntu2.1), libunity-2d-private0:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), libcheese3:i386 (3.4.1-0ubuntu2, 3.4.1-0ubuntu2.1), gvfs-libs:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), unity-2d-shell:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), unity-2d-common:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), gvfs-bin:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), gvfs-common:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), gvfs-daemons:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), grub-pc:i386 (1.99-21ubuntu3.1, 1.99-21ubuntu3.4), ubuntu-keyring:i386 (2011.11.21, 2011.11.21.1), wine1.5-i386:i386 (1.5.13-0ubuntu1, 1.5.14-0ubuntu1), unity-2d-spread:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), software-properties-common:i386 (0.82.7.2, 0.82.7.3), gstreamer0.10-plugins-bad:i386 (0.10.22.3-2ubuntu2, 0.10.22.3-2ubuntu2.1), libgstreamer-plugins-bad0.10-0:i386 (0.10.22.3-2ubuntu2, 0.10.22.3-2ubuntu2.1), grub-pc-bin:i386 (1.99-21ubuntu3.1, 1.99-21ubuntu3.4), software-properties-gtk:i386 (0.82.7.2, 0.82.7.3), libcheese-gtk21:i386 (3.4.1-0ubuntu2, 3.4.1-0ubuntu2.1), gvfs:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), gvfs-backends:i386 (1.12.1-0ubuntu1, 1.12.1-0ubuntu1.1), grub-common:i386 (1.99-21ubuntu3.1, 1.99-21ubuntu3.4), unity-2d-places:i386 (5.12.0-0ubuntu1.1, 5.12.0-0ubuntu1.2), xserver-xorg-video-intel:i386 (2.20.8~precise~ppa2, 2.20.9~precise~ppa1)
End-Date: 2012-10-01  20:54:14

Start-Date: 2012-10-03  15:02:41
Commandline: apt-get install openconnect
Install: openconnect:i386 (3.15-0ubuntu2), libopenconnect1:i386 (3.15-0ubuntu2, automatic)
End-Date: 2012-10-03  15:03:01

Start-Date: 2012-10-03  15:07:04
Commandline: apt-get install network-manager-openconnect
Install: network-manager-openconnect-gnome:i386 (0.9.4.0-0ubuntu1, automatic), network-manager-openconnect:i386 (0.9.4.0-0ubuntu1)
End-Date: 2012-10-03  15:07:09

Start-Date: 2012-10-04  00:05:07
Commandline: aptdaemon role='role-remove-packages' sender=':1.79'
Remove: xpad:i386 (4.0-5ubuntu2)
End-Date: 2012-10-04  00:05:43

Start-Date: 2012-10-04  00:05:47
Commandline: aptdaemon role='role-remove-packages' sender=':1.79'
Remove: gnumeric:i386 (1.10.17-1ubuntu2)
End-Date: 2012-10-04  00:06:00

Start-Date: 2012-10-04  00:08:00
Commandline: aptdaemon role='role-remove-packages' sender=':1.85'
Remove: xfce4-xkb-plugin:i386 (0.5.4.3-1ubuntu1), xfce4-verve-plugin:i386 (1.0.0-1), xfce4-panel:i386 (4.8.6-2ubuntu2), xfce4-mailwatch-plugin:i386 (1.1.0-5), thunar-volman:i386 (0.6.1-0ubuntu1), xfce4-notes-plugin:i386 (1.7.7-2ubuntu1), orage:i386 (4.8.3-1), xfce4-weather-plugin:i386 (0.7.4-3), xfce4-netload-plugin:i386 (1.1.0-1), thunar-archive-plugin:i386 (0.3.0-4), xfce4-indicator-plugin:i386 (0.4.0-0ubuntu2), thunar:i386 (1.2.3-3ubuntu2), xfce4-notes:i386 (1.7.7-2ubuntu1), xfce4-systemload-plugin:i386 (1.0.0-1ubuntu1), thunar-media-tags-plugin:i386 (0.2.0-1), xubuntu-desktop:i386 (2.152), xfce4-cpugraph-plugin:i386 (1.0.1-2), xfce4-datetime-plugin:i386 (0.6.1-3ubuntu1), xfdesktop4:i386 (4.8.3-2ubuntu7), xfce4-quicklauncher-plugin:i386 (1.9.4-9), exo-utils:i386 (0.6.2-4), xfce4-utils:i386 (4.8.3-1ubuntu2), xfce4-terminal:i386 (0.4.8-1ubuntu1), xfce4-places-plugin:i386 (1.2.0-3), xfce4-dict:i386 (0.6.0-5)
End-Date: 2012-10-04  00:08:32

Start-Date: 2012-10-04  00:08:38
Commandline: aptdaemon role='role-remove-packages' sender=':1.85'
Remove: thunderbird-globalmenu:i386 (15.0.1+build1-0ubuntu0.12.04.1), thunderbird:i386 (15.0.1+build1-0ubuntu0.12.04.1)
End-Date: 2012-10-04  00:08:43

Start-Date: 2012-10-04  00:08:51
Commandline: aptdaemon role='role-remove-packages' sender=':1.85'
Remove: pidgin-libnotify:i386 (0.14-4ubuntu10), libotr2:i386 (3.2.0-4ubuntu0.1), pidgin:i386 (2.10.3-0ubuntu1.1), pidgin-otr:i386 (3.2.0-5ubuntu0.12.04.1)
End-Date: 2012-10-04  00:09:03

Start-Date: 2012-10-04  00:09:19
Commandline: aptdaemon role='role-remove-packages' sender=':1.85'
Remove: libots0:i386 (0.5.0-2.1), abiword:i386 (2.9.2+svn20120213-1), abiword-plugin-mathview:i386 (2.9.2+svn20120213-1), libabiword-2.9:i386 (2.9.2+svn20120213-1), libgoffice-0.8-8:i386 (0.8.17-1), libloudmouth1-0:i386 (1.4.3-8), link-grammar-dictionaries-en:i386 (4.7.4-2), libtidy-0.99-0:i386 (20091223cvs-1ubuntu2), libwv-1.2-4:i386 (1.2.9-2), libgdome2-0:i386 (0.8.1+debian-4.1build1), libgsf-1-common:i386 (1.14.21-2), abiword-plugin-grammar:i386 (2.9.2+svn20120213-1), libgdome2-cpp-smart0c2a:i386 (0.2.6-6build2), liblink-grammar4:i386 (4.7.4-2), libgtkmathview0c2a:i386 (0.8.0-7), libgsf-1-114:i386 (1.14.21-2)
End-Date: 2012-10-04  00:09:33

Start-Date: 2012-10-04  00:09:55
Commandline: aptdaemon role='role-remove-packages' sender=':1.85'
Remove: rhythmbox:i386 (2.96-0ubuntu4.2), rhythmbox-mozilla:i386 (2.96-0ubuntu4.2), rhythmbox-plugin-zeitgeist:i386 (2.96-0ubuntu4.2), rhythmbox-plugin-cdrecorder:i386 (2.96-0ubuntu4.2), rhythmbox-plugins:i386 (2.96-0ubuntu4.2), rhythmbox-plugin-magnatune:i386 (2.96-0ubuntu4.2)
End-Date: 2012-10-04  00:10:05

Start-Date: 2012-10-04  12:50:10
Commandline: apt-get install pacman
Install: pacman:i386 (10-17ubuntu2)
End-Date: 2012-10-04  12:50:24

Start-Date: 2012-10-04  12:52:54
Commandline: apt-get install xfce4-utils
Install: xfce4-panel:i386 (4.8.6-2ubuntu2, automatic), thunar-volman:i386 (0.6.1-0ubuntu1, automatic), thunar:i386 (1.2.3-3ubuntu2, automatic), exo-utils:i386 (0.6.2-4, automatic), xfce4-utils:i386 (4.8.3-1ubuntu2)
End-Date: 2012-10-04  12:53:20

Start-Date: 2012-10-04  14:02:14
Commandline: apt-get install xfdesktop4
Install: xfdesktop4:i386 (4.8.3-2ubuntu7)
End-Date: 2012-10-04  14:02:19

Start-Date: 2012-10-04  14:28:45
Commandline: apt-get install xfce4-mixer
Install: xfce4-mixer:i386 (4.8.0-2ubuntu1)
End-Date: 2012-10-04  14:28:51
```Oh god, do i have to install xcfe again?

---

### Post by ajgreeny on 2012-10-04
You were caught by the problem of applications being removed and taking lots of other applications and utilities with them because of dependencies.  It is always worth noting carefully what packages will also be removed when you uninstall anything.

Just run ```
sudo apt-get install xubuntu-desktop
``` again, or even better as it allows you to see more clearly what is going to happen, use synaptic to install or reinstall xubuntu-desktop.  That should get you back where you were.

---

### Post by raspatan on 2012-10-04
Thank you very much!!! I used synaptic for this and I guess I installed what seemed to me important. It works fine now. 
Because I'm new on linux, when the software suggest me to do something I usually do it. Next time I will try to be more cautious. 

):P):P:p

---

