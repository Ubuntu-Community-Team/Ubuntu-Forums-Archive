---
title: "Multiple failures after minor upgrade in Natty"
date: 2011-10-15
forum: General Help
---

### Post by quequotion on 2011-10-15
What in the world... Last night I upgraded a few packages in Natty.

Pulseaudio is refusing connections to everything. The daemon is running just fine according to the system log, but nothing can access it. I have no sound capabilities.

Gnome-settigns-daemon has lost its mind. I can't get rid of the default Ubuntu background although the background is disabled for gdm, gnome desktop, nautilus, and compiz. I found seven gnome-settings-daemon processes running after I tried to kill and restart it.

Firefox freezes if i try to open a right-click menu or a tab.

GRUB had to be reinstalled from the livecd after it vanished (again).

---

### Post by quequotion on 2011-10-15
here's the update that shattered my system:

```
Commit Log for Fri Oct 14 19:32:07 2011


Downgraded the following packages:
indicator-sensors

Upgraded the following packages:
banshee (2.2.0+git20111002.r1.dc07b15-0ubuntu1+natty) to 2.2.0+git20111013.r1.aaee9b3-0ubuntu1+natty
banshee-community-extensions (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-alarm (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-ampache (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-appindicator (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-awn (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-clutterflow (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-coverwallpaper (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-jamendo (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-karaoke (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-lastfmfingerprint (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-lcd (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-lirc (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-liveradio (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-lyrics (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-magnatune (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-mirage (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-openvp (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-radiostationfetcher (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-randombylastfm (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-soundmenu (2.2.0+git20111002.r1.dc07b15-0ubuntu1+natty) to 2.2.0+git20111013.r1.aaee9b3-0ubuntu1+natty
banshee-extension-streamrecorder (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-telepathy (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extension-ubuntuonemusicstore (2.2.0+git20111002.r1.dc07b15-0ubuntu1+natty) to 2.2.0+git20111013.r1.aaee9b3-0ubuntu1+natty
banshee-extension-zeitgeistdataprovider (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
banshee-extensions-common (2.2.0+git20111002.r1.8119051-0ubuntu1+natty) to 2.2.0+git20111011.r1.f19eb77-0ubuntu1+natty1
classicmenu-indicator (0.04) to 0.05
libdvdread4 (4.1.3-10ubuntu3) to 4.1.3-10ubuntu3.1
libimobiledevice2 (1.1.0-3) to 1.1.0-3ubuntu1
libsyncdaemon-1.0-1 (1.6.2-0ubuntu1) to 1.6.2-0ubuntu2
libvlc5 (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1
libvlccore4 (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1
nvidia-current (280.13-0ubuntu1~natty~xup1) to 285.05.09-0ubuntu1~natty~xup1
nvidia-settings (280.13-0ubuntu1~natty~xup1) to 285.05.09-0ubuntu1~natty~xup1
python-ubuntuone-client (1.6.2-0ubuntu1) to 1.6.2-0ubuntu2
sixad (1.4.97+git20110701-0~natty1) to 1.5.1-0ubuntu1~natty1
ubuntuone-client (1.6.2-0ubuntu1) to 1.6.2-0ubuntu2
ubuntuone-client-gnome (1.6.2-0ubuntu1) to 1.6.2-0ubuntu2
unity (3.8.16-0ubuntu1~natty2) to 3.8.16-0ubuntu1~natty3
unity-common (3.8.16-0ubuntu1~natty2) to 3.8.16-0ubuntu1~natty3
vlc (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1
vlc-data (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1
vlc-nox (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1
vlc-plugin-notify (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1
vlc-plugin-pulse (1.1.11-1~getdeb1) to 1.1.12-1~getdeb1

Installed the following packages:
deja-dup (18.1.1-0ubuntu1.1)
duplicity (0.6.13-0ubuntu1.1)
librsync1 (0.9.7-7)
python-boto (1.9b-1ubuntu5)
python-rackspace-cloudfiles (1.5.1-0ubuntu2)
```

I'm a little suspicious of unity, unity-common and nvidia-current; not that those packages should be capable of ruining a computer as completely as mine has been, but I have past experience with these packages causing other problems.

---

### Post by quequotion on 2011-10-16
Since the situation in Natty seemed hopless, I went ahead and upgraded to Oneiric.

This didn't fix anything. This made things much worse. Luckliy, I don't give up so easily.

I managed to get pulseaudio working after deleting it and everything associated with it, then reinstalling. Still no clue why the daemon was running but no one had permission to use it.

I've reinstalled GRUB from the live CD a few more times. It seems to dissappear after a random number of boots or a certain number of boot failures.

gnome-settings-daemon may or may not be working. Everything looks fine but I always worry about what this daemon is actually doing (or not doing).

I haven't reinstalled firefox yet as I am too busy fixing things to use a potentially broken browser. Epiphany will do for now.

Compiz in Oneiric is horribly broken with nvidia. Windows, menus, panels, and notifications will not redraw unless dragged or the cube is rotated. Any animations stop after their frist frame, fade ins/outs make things invisible, and menus are useless.

---

### Post by quequotion on 2011-10-19
Firefox reinstalled well and even maintained my extensions and preferences after "apt-get remove --purge firefox".

Very little progress with compiz. Found a lot of bug reports for the same issue in 2007~8 but dealing with different hardware and the solutions didn't work for me.

Why doesn't compiz redraw?

[I have found a way]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875564") to force redraw by enabling the cube-gears decoration, but performance is rather poor (compiz will only refresh as fast as the gears will spin) and the gears are severely glitched.

---

### Post by quequotion on 2011-11-05
No longer having this after complete annihilation and fresh install of 11.10.

Another shameful full reinstall.

---

