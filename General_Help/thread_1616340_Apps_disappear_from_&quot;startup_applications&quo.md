---
title: "Apps disappear from &quot;startup applications&quot; list"
date: 2010-11-08
forum: General Help
---

### Post by pmooney78 on 2010-11-08
I've been trying to add applications to my "Startup Applications" menu. Most of the time, they "stick," but sometimes simply disappear, either immediately or after a variable length of time (sometimes more or less immediately, sometimes after several restarts, or anywhere in between). I've noticed that, when they stop booting, their entry disappears from ~/.config/autostart, but changing permissions on the affected files (e.g., removing write access) doesn't seem to help.

Any suggestions? Re-adding the same things over and over gets frustrating after a while, and I can't figure out why these entries are disappearing.

Currently running Ubuntu 9.10 on an HP Pavilion dv6000 with an Intel Centrino Core Duo processor and 2 GB of RAM. Any help much appreciated.

---

### Post by pmooney78 on 2010-11-09
Any suggestions?

---

### Post by pmooney78 on 2010-11-10
Anyone?

---

### Post by pmooney78 on 2010-11-13
Or is there another way to auto-load programs when X starts?

---

### Post by pmooney78 on 2010-11-14
anyone?

---

### Post by pmooney78 on 2010-11-15
Bump.

---

### Post by realzippy on 2010-11-15
Never heard about this issue,never happened to me.,,,guess it is related
to changes you made (permissions,what have you done exactly?Anything else you modified?)

Claim that your issue cannot happen to a "vanilla" ubuntu....

---

### Post by matt_symes on 2010-11-15
Hi

Yes, that is strange. 

Is there anything in the  ~/.xsession-errors file around the time it happens? Or any of the other logs?

Is it the same entries that keep disappearing, all the entries? What are those entries?

And has been asked what permissions are you using?

Kind regards

---

### Post by eeBus on 2010-11-19
A few of my applications have disappeared too. Tasque; Bleach Bit; Krusader. They don't all disappear at the same time, and since I don't use them all the time I can't identify when, or what triggers the disappearance. I would say that the problems have started after doing my first backup with sbackup (Simple Backup)

I'm on 10.04 LTS

---

### Post by pmooney78 on 2010-11-22
I've re-added several applications to the startup list and am waiting for them to disappear again -- it's taking longer than I thought; apologies for the delay in replying. Perhaps the problem has simply disappeared; if I don't see something go missing from the list in the next few days, I'll assume that's what happened. Apologies for the delay.

This is, in fact, a "plain vanilla" installation -- I reinstalled from scratch several weeks before it started happening.

---

### Post by pmooney78 on 2010-11-23
OK, the launcher for caffeine just disappeared from ~/.config/autostart again. There are errors noted in ~/.xsession-errors, but nothing seems to indicate directly that anything was removed from that folder. Here's the file anyway:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-26ZpD2/socket
SSH_AUTH_SOCK=/tmp/keyring-26ZpD2/socket.ssh

(gnome-settings-daemon:2271): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(polkit-gnome-authentication-agent-1:2375): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2375): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(nautilus:2360): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Starting gtk-window-decorator
sendto: Network is unreachable

(thunderbird-bin:2421): GLib-WARNING **: g_set_prgname() called multiple times
** (gnome-panel:2359): DEBUG: Adding applet 0.
** (gnome-panel:2359): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:2359): DEBUG: Adding applet 1.
** (gnome-panel:2359): DEBUG: Adding applet 2.
** (gnome-panel:2359): DEBUG: Adding applet 3.
** (gnome-panel:2359): DEBUG: Adding applet 4.
** (gnome-panel:2359): DEBUG: Adding applet 5.
Initializing nautilus-gdu extension

** (nautilus:2360): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2360): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2360): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** (gnome-panel:2359): DEBUG: Adding applet 6.
** (gnome-panel:2359): DEBUG: Adding applet 7.
** (gnome-panel:2359): DEBUG: Adding applet 8.
** (gnome-panel:2359): DEBUG: Adding applet 9.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
** (nm-applet:2391): DEBUG: foo_client_state_changed_cb
I/O warning : failed to load external entity "/home/patrick/.compiz/session/109daae02639a603fe129049699189937500000021880035"
** (nm-applet:2391): DEBUG: foo_client_state_changed_cb
** (gnome-panel:2359): DEBUG: Adding applet 10.
** (gnome-panel:2359): DEBUG: Adding applet 11.
** (gnome-panel:2359): DEBUG: Adding applet 12.
** (gnome-panel:2359): DEBUG: Adding applet 13.
** (gnome-panel:2359): DEBUG: Adding applet 14.
** (gnome-panel:2359): DEBUG: Adding applet 15.

(firefox-bin:2827): GLib-WARNING **: g_set_prgname() called multiple times
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=956890411&utmhn=30boxes.com& {snip}, should be HTTPS!
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=1320909690&utmhn=www.last.fm& {snip} , should be HTTPS!
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=483574012&utmhn=www.last.fm& {snip}, should be HTTPS!
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=995249103&utmhn=ubuntuforums.org&utmcs=ISO-8859-1&utmsr=1280x800&utmsc=24-bit&utmul=en-us&utmje=1& {snip}, should be HTTPS!

(nautilus:3071): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

(nautilus:2360): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed

** (nautilus:2360): CRITICAL **: dbus_g_proxy_begin_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=947715201&utmhn=ubuntuforums.org& {snip}, should be HTTPS!
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=1555608622&utmhn=ubuntuforums.org& {snip}, should be HTTPS!
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=1650210295&utmhn=www.okcupid.com& {snip}, should be HTTPS!
Aborting possible favicon http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=785037629&utmhn=www.okcupid.com& {snip}, should be HTTPS!

```

It's all more or less gibberish to me, anyway, and none of the other logs have anything that's obviously related. Any suggestions?

---

### Post by pmooney78 on 2010-11-26
Any suggestions?

---

### Post by CrushingYourHead on 2011-05-16
Anybody else currently having this problem? I've been having it for awhile now...

I've tried fresh installs of Ubuntu 10.04.2(Gnome 2.30.2) and Ubuntu 10.10(Gnome 2.32). Both are having the issue. Anytime I make a manual entry (google-chrome) to the Startup Applications list, it will disappear with 2 or 3 reboots. Sometimes after just 1.

Just as a side-note: I've tried one of those OpenSuse-based Chrome OS inspired install disks as a test. It happened there as well. It happened to be using Gnome 2.32

Any ideas would be appreciated :)

---

### Post by CrushingYourHead on 2011-05-16
I only seem to be having the issue on my Dell Latitude D610. On a generic Intel Duo-Core box, the google-chrome entry stays in the Startup list. Could this possibly be hardware specific?

Anyone?

---

### Post by gunther123 on 2011-05-26
I just installed a brand new instance of 11.04 on a Centrino Duo laptop.  The only customizations I have made was to install Google Chrome and change the default session to classic.  When I add Google Chrome to the startup applications, it works for one reboot and then disappears from the startup applications.  I can consistently repeat.

---

### Post by seul on 2011-05-30
> **gunther123 said:**
> I just installed a brand new instance of 11.04 on a Centrino Duo laptop.  The only customizations I have made was to install Google Chrome and change the default session to classic.  When I add Google Chrome to the startup applications, it works for one reboot and then disappears from the startup applications.  I can consistently repeat.

Same here with chromium on a T60. I tried both »chromium-browser« and »/usr/bin/chromium-browser %U« with the same result. Thunderbird and Yakuake were added manually and they stick.

---

### Post by pmooney78 on 2011-06-14
I reinstalled a few months ago and haven't been having this problem since. One of the primary applications I was having the problem with was Caffeine, but I found a separate fix for that: Caffeine disappears from the autostart list when I add it directly through System / Preferences / Startup Applications, but stays in when I ask it to autostart in the Caffeine preferences. My theory there is that Caffeine is internally maintaining its own expectations about whether it's supposed to autostart, based on whether the user has indicated this in preferences, and removing itself from the GNOME startup programs if I haven't asked it to autostart through its own mechanism.

---

### Post by rvboutin on 2012-08-12
Hi,
Fresh install of Ubuntu 12.04LTS... and the problem persists!!
I am trying to add 2 command lines to mount partitions @ startup but only1 of them will stick in the startup application list, the 2nd one disappears as soon as I close the window!!
Any suggestion anyone?
Cheers,
Rv

---

### Post by oldos2er on 2012-08-12
Please start a new thread; this one's two years old.

---

