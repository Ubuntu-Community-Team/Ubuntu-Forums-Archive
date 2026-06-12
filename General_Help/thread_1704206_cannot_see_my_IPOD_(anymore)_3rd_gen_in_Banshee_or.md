---
title: "cannot see my IPOD (anymore) 3rd gen in Banshee or Nautilus (10.10)"
date: 2011-03-10
forum: General Help
---

### Post by ptitdoon on 2011-03-10
Hi,

Everything worked fine with my IPOD for more than a year. Since a particular event of which I have no idea, I cannot see it anymore (in Banshee or Nautilus). However the IPOD does display "connected" on its screen.

I looked to this [topic]("http://ubuntuforums.org/showthread.php?t=1677258&highlight=ipod+mounted") (and others), but nothing helped. I actually did
```
sudo add-apt-repository ppa:pmcenery/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```Here is what I got with **lsusb**:
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 003: ID 05ac:1262 Apple, Inc. iPod Nano 3.Gen**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 05ac:0221 Apple, Inc. Aluminum Keyboard (ISO)
Bus 001 Device 010: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 009: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 008: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 007: ID 046d:c525 Logitech, Inc. MX Revolution Cordless Mouse
Bus 001 Device 006: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 005: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 001 Device 003: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 002: ID 413c:2513 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I have pretty much no idea of what to do, and before doing anything stupid I am looking for help which will be be really appreciated!

Thanks a lot!
Denis

---

### Post by phisher1 on 2011-03-10
I am seeing the same problem now.

I previously added the ppa:pmcenery/ppa and ran any applicable updates and that did fix the problem. Now after some recent updates, my iPhone 4 running 4.2.1 is not being recognized.

I don't reboot that often even when I get a new kernel.. but I'm betting the package that broke support is one of these:


Start-Date: 2011-03-01  08:08:42
Upgrade: libsmbclient:amd64 (3.5.4~dfsg-1ubuntu8.2, 3.5.4~dfsg-1ubuntu8.3), smbclient:amd64 (3.5.4~dfsg-1ubuntu8.2, 3.5.4~dfsg-1ubuntu8.3), libwbclient0:amd64 (3.5.4~dfsg-1ubuntu8.2, 3.5.4~dfsg-1ubuntu8.3), libfuse2:amd64 (2.8.4-1ubuntu1.2, 2.8.4-1ubuntu1.3), samba-common:amd64 (3.5.4~dfsg-1ubuntu8.2, 3.5.4~dfsg-1ubuntu8.3), samba:amd64 (3.5.4~dfsg-1ubuntu8.2, 3.5.4~dfsg-1ubuntu8.3), samba-common-bin:amd64 (3.5.4~dfsg-1ubuntu8.2, 3.5.4~dfsg-1ubuntu8.3), fuse-utils:amd64 (2.8.4-1ubuntu1.2, 2.8.4-1ubuntu1.3)
End-Date: 2011-03-01  08:09:13

Start-Date: 2011-03-02  11:42:18
Install: linux-headers-2.6.35-27-generic:amd64 (2.6.35-27.48), linux-headers-2.6.35-27:amd64 (2.6.35-27.48), linux-image-2.6.35-27-generic:amd64 (2.6.35-27.48)
Upgrade: linux-generic:amd64 (2.6.35.25.32, 2.6.35.27.35), linux-headers-generic:amd64 (2.6.35.25.32, 2.6.35.27.35), linux-image-generic:amd64 (2.6.35.25.32, 2.6.35.27.35), linux-libc-dev:amd64 (2.6.35-1025.44, 2.6.35-1027.48)
End-Date: 2011-03-02  11:44:21

Start-Date: 2011-03-03  09:39:52
Upgrade: firefox-branding:amd64 (3.6.13+build3+nobinonly-0ubuntu0.10.10.1, 3.6.14+build3+nobinonly-0ubuntu0.10.10.1), firefox:amd64 (3.6.13+build3+nobinonly-0ubuntu0.10.10.1, 3.6.14+build3+nobinonly-0ubuntu0.10.10.1), libpango1.0-common:amd64 (1.28.2-0ubuntu1, 1.28.2-0ubuntu1.1), xulrunner-1.9.2:amd64 (1.9.2.13+build3+nobinonly-0ubuntu0.10.10.1, 1.9.2.14+build3+nobinonly-0ubuntu0.10.10.1), gir1.0-pango-1.0:amd64 (1.28.2-0ubuntu1, 1.28.2-0ubuntu1.1), google-chrome-beta:amd64 (10.0.648.114-r75702, 10.0.648.126-r76502), libpango1.0-0:amd64 (1.28.2-0ubuntu1, 1.28.2-0ubuntu1.1), firefox-gnome-support:amd64 (3.6.13+build3+nobinonly-0ubuntu0.10.10.1, 3.6.14+build3+nobinonly-0ubuntu0.10.10.1)
End-Date: 2011-03-03  09:40:26

Start-Date: 2011-03-03  15:01:43
Commandline: apt-get install dselect
Install: dselect:amd64 (1.15.8.4ubuntu3.1)
End-Date: 2011-03-03  15:01:49

Start-Date: 2011-03-04  07:49:55
Install: chromium-browser-l10n:amd64 (9.0.597.107~r75357-0ubuntu0.10.10.1)
Upgrade: poppler-utils:amd64 (0.14.3-0ubuntu1.1, 0.14.3-0ubuntu1.2), chromium-browser:amd64 (9.0.597.94~r73967-0ubuntu0.10.10.1, 9.0.597.107~r75357-0ubuntu0.10.10.1), linux-firmware:amd64 (1.38.3, 1.38.4), chromium-codecs-ffmpeg:amd64 (0.6+svn20101129r67548+69665-0ubuntu0.10.10.1, 9.0.597.107~r75357-0ubuntu0.10.10.1), libpoppler7:amd64 (0.14.3-0ubuntu1.1, 0.14.3-0ubuntu1.2), libpoppler-glib5:amd64 (0.14.3-0ubuntu1.1, 0.14.3-0ubuntu1.2), google-chrome-beta:amd64 (10.0.648.126-r76502, 10.0.648.127-r76697), chromium-browser-inspector:amd64 (9.0.597.94~r73967-0ubuntu0.10.10.1, 9.0.597.107~r75357-0ubuntu0.10.10.1)
End-Date: 2011-03-04  07:50:33

Start-Date: 2011-03-08  08:38:37
Upgrade: python-avahi:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), libavahi-glib1:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), firefox-branding:amd64 (3.6.14+build3+nobinonly-0ubuntu0.10.10.1, 3.6.15+build1+nobinonly-0ubuntu0.10.10.1), avahi-utils:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), libavahi-common-data:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), libavahi-core7:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), firefox:amd64 (3.6.14+build3+nobinonly-0ubuntu0.10.10.1, 3.6.15+build1+nobinonly-0ubuntu0.10.10.1), libavahi-ui0:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), xulrunner-1.9.2:amd64 (1.9.2.14+build3+nobinonly-0ubuntu0.10.10.1, 1.9.2.15+build1+nobinonly-0ubuntu0.10.10.1), libtiff4:amd64 (3.9.4-2, 3.9.4-2ubuntu0.1), avahi-daemon:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), libavahi-client3:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), libavahi-gobject0:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), avahi-autoipd:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), libavahi-common3:amd64 (0.6.27-2ubuntu3, 0.6.27-2ubuntu3.1), firefox-gnome-support:amd64 (3.6.14+build3+nobinonly-0ubuntu0.10.10.1, 3.6.15+build1+nobinonly-0ubuntu0.10.10.1)
End-Date: 2011-03-08  08:39:15

---

### Post by ptitdoon on 2011-03-11
Anbody knows where to start to look at?

---

