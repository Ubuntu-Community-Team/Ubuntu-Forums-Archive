---
title: "Update/Restart breaks desktop, SVG, nautilus, other random packages"
date: 2012-02-03
forum: General Help
---

### Post by fxb9500 on 2012-02-03
So after performing some routine updates just now I have found that my desktop configuration is broken, and several programs don't work.

The overall appearance of Ubuntu seems to have changed.  The icons aren't the same.  When I try to browse to various locations such as computer or network, Nautilus gives me, "Nautilus cannot handle "computer" locations.".  Docky is no longer working, or does anything at all.  Shutter returns the following error message when I try to start it: "Error while opening image 'sel_window_tooltip.svg'."  USB mounting doesn't seem to work anymore.

[IMG]http://i.imgur.com/QLiNN.png[/IMG]  

... Is what I am getting, rather than the default icons:

[IMG]http://i.imgur.com/XE88F.png[/IMG]

Apologies in advance for a long post.

Here is my apt/history.log:
```

Start-Date: 2012-02-02  21:23:43
Install: libtagc0:amd64 (1.6.3-1, automatic), libkarma0:amd64 (0.0.6-4.5), libboo2.0.9-cil:amd64 (0.9.2.3383+dfsg-1)
Upgrade: xserver-xorg-video-all:amd64 (7.6+4ubuntu3.1, 7.6+4ubuntu3.2), usbmuxd:amd64 (1.0.7-1, 1.0.7-1ubuntu0.11.04.1), libicu44:amd64 (4.4.2-2, 4.4.2-2ubuntu0.11.04.1), libgpod-common:amd64 (0.8.0-2ubuntu0.1, 0.8.0-3~hyper1+natty), python-software-properties:amd64 (0.80.9, 0.80.9.1), libgpod4:amd64 (0.8.0-2ubuntu0.1, 0.8.0-3~hyper1+natty), banshee:amd64 (2.0.0-2ubuntu2, 2.2.1-1ubuntu2~hyper1+natty), xserver-xorg-input-all:amd64 (7.6+4ubuntu3.1, 7.6+4ubuntu3.2), spotify-client-qt:amd64 (0.6.2.291.gcccc1f5.116-1, 0.6.6.10.gbd39032.58-1), banshee-extension-soundmenu:amd64 (2.0.0-2ubuntu2, 2.2.1-1ubuntu2~hyper1+natty), software-properties-gtk:amd64 (0.80.9, 0.80.9.1), xserver-xorg:amd64 (7.6+4ubuntu3.1, 7.6+4ubuntu3.2), banshee-extension-ubuntuonemusicstore:amd64 (2.0.0-2ubuntu2, 2.2.1-1ubuntu2~hyper1+natty), libusbmuxd1:amd64 (1.0.7-1, 1.0.7-1ubuntu0.11.04.1), x11-common:amd64 (7.6+4ubuntu3.1, 7.6+4ubuntu3.2), xorg:amd64 (7.6+4ubuntu3.1, 7.6+4ubuntu3.2)
End-Date: 2012-02-02  21:24:46

Start-Date: 2012-02-02  22:15:06
Commandline: /usr/sbin/synaptic
Install: libgd-gd2-perl:amd64 (2.41-1, automatic), librsvg2-bin:amd64 (2.32.1-0ubuntu3.1), libsvg-perl:amd64 (2.50-1, automatic), emelfm2-svg-icons:amd64 (20100219-1), libgd-svg-perl:amd64 (0.33-1)
End-Date: 2012-02-02  22:15:17

Start-Date: 2012-02-02  22:19:34
Install: libnet-dbus-glib-perl:amd64 (0.33.0-1)
End-Date: 2012-02-02  22:19:38

Start-Date: 2012-02-02  22:39:58
Commandline: /usr/sbin/synaptic
Remove: libgtkmm-2.4-dev:amd64 (2.24.0-0ubuntu1), python-gtk2-dev:amd64 (2.22.0-0ubuntu1.1), libgdk-pixbuf2.0-dev:amd64 (2.23.3-0ubuntu1), libglade2-dev:amd64 (2.6.4-1build1), libgtk2.0-dev:amd64 (2.24.4-0ubuntu2)
End-Date: 2012-02-02  22:40:04

Start-Date: 2012-02-02  22:44:52
Commandline: /usr/sbin/synaptic
Install: libjpeg8:amd64 (8b-1)
End-Date: 2012-02-02  22:44:55

```

I've also built the most current libraries for GDK since the reboot prior to this breaking one.  

If anyone know or could help me find what has changed to cause these problems, I would really appreciate it.

I really like Ubuntu, but it's times like these that make me want to leave Linux all together.

---

