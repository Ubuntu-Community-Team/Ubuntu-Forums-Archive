---
title: "Broken indicator applet and indicator applet session"
date: 2010-07-09
forum: General Help
---

### Post by sharq1 on 2010-07-09
After some updates I can't get indicator applet and session management applet working, I get these instead:

[IMG]http://img341.imageshack.us/img341/4350/tmpdzalbn.png[/IMG]

I tried to pull back any updates, but it changed nothing. I installed older (lucid) versions of these packages:

```
indicator-applet
indicator-applet-complete
indicator-sound
indicator-applet-session
libevdocument2
gnome-panel-data
libecal1.2-7
libevview2
libgdata-google1.2-1
libedata-cal1.2-6
vinagre
libsoup-gnome2.4-1
xserver-xorg-video-intel
libgp11-0
gnome-about
libgcr0
libgnome-desktop-2-17
libedataserverui1.2-8
libpanel-applet2-0
libedata-book1.2-2
libegroupwise1.2-13
libexchange-storage1.2-3
libusb-0.1-4
fglrx-modaliases
libgnome-keyring0
gnome-desktop-data
libcamel1.2-14
gnome-panel
libebackend1.2-0
libpam-gnome-keyring
libgdata1.2-1
libedataserver1.2-11
libsoup2.4-1
libebook1.2-9
```

I found out, that someone else had similar problem some time ago, but it looks like unsolved:
[http://ubuntuforums.org/showthread.php?t=1437302]("http://ubuntuforums.org/showthread.php?t=1437302")

Also, there is no volume settings applet

I would greatly appreciate if any of you could help out.
Thanks.

---

### Post by ajgreeny on 2010-07-09
> I tried to pull back any updates, but it changed nothing. I installed  older (lucid) versions of these packages:
Can I assume from this that you are running 10.10?

If so, you should not be surprised that things break.  Meerkat is an alpha OS at the moment and breakages are almost to be expected.  Having said all that I can't offer any more concrete help, I'm afraid, other than to say this should really be in the Meerkat section of the forum, not in General help

---

### Post by sharq1 on 2010-07-09
I'm using Lucid Lynx (10.04). I ment that i installed standard lucid versions of packages, not the upgraded ones.

---

### Post by ajgreeny on 2010-07-09
OK, thanks.
However, I'm sorry, but I don't think I can help with your query.

---

### Post by lidex on 2010-07-09
Sorry I can't decipher those error messages but they look like the ones you get when you have old gconf config files referring to something no longer there. You should really update your packages to the current versions:
```
sudo apt-get update
sudo apt-get upgrade
``` 
Now make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session
```
Now reset your panels:
```
gconftool-2 --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
Next right-click on your panel and select 'Add to panel' and add back items that are missing. Indicator applet I believe should have volume control, but you may need to play around as there are three indicator entries in my add list. You may want to search synaptic for 'applet' to find any that are not in the list as they have to be installed to appear there.

---

### Post by sharq1 on 2010-07-10
I really hoped that this will help, but it changed nothing :( Still the same messages.

---

### Post by eyehavenoi on 2010-07-12
> **lidex said:**
> Sorry I can't decipher those error messages but they look like the ones you get when you have old gconf config files referring to something no longer there. You should really update your packages to the current versions:
```
sudo apt-get update
sudo apt-get upgrade
```Now make sure these are installed:
```
sudo apt-get install --reinstall gnome-media gnome-media-common indicator-applet indicator-applet-session indicator-me indicator-session
```Now reset your panels:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```Next right-click on your panel and select 'Add to panel' and add back items that are missing. Indicator applet I believe should have volume control, but you may need to play around as there are three indicator entries in my add list. You may want to search synaptic for 'applet' to find any that are not in the list as they have to be installed to appear there.

This is exactly what I needed to re-install my applet. I tried to eliminate the mail icon and screwed up the whole applet, I was getting error messages and the applet wasn't loading...

I'm on 10.04 as well... Can't imagine why a re-install wouldn't solve the issue with the original poster.

---

### Post by sharq1 on 2010-07-12
I ran gnome-panel from terminal and added indicator-applet, and this is output:

```
** (gnome-panel:24477): WARNING **: panel-applet-frame.c:1363: failed to load applet OAFIID:GNOME_IndicatorApplet (cannot get popup component):
Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'

(gnome-panel:24477): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().

```

---

### Post by sharq1 on 2010-07-19
There were some updates of gnome-panel and gnome-panel related packages, but problem is still the same. Any ideas?

---

### Post by leafnode on 2010-07-19
Same here on ubuntu netbook remix updated to 10.04 - all related packages in most current version from the repository, commands mentioned above didn't help.

---

### Post by lidex on 2010-07-22
I missed one. For volume control applet:
```
sudo apt-get install indicator-sound
```

Logout/in

---

### Post by leafnode on 2010-07-23
Didn't help either. Is there any help/tutorial I could read to know how to debug this problem? I'm a programmer myself, but I don't have much experience with X/applet programming.

---

