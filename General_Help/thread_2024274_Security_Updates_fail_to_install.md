---
title: "Security Updates fail to install"
date: 2012-07-13
forum: General Help
---

### Post by Silvernail on 2012-07-13
Oneiric
Gnome3

I am haveing trouble installing some updates.
Running from a terminal ( as suggested in another thread ):
```
sudo apt-get update && sudo apt-get upgrade
```
produces this at the end of the terminal display.
> 
Fetched 12.7 MB in 36s (348 kB/s)                                                                                                                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  icedtea-netx icedtea-plugin icedtea6-plugin
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
dave@dave:~$ 
These 3 :
>   icedtea-netx icedtea-plugin icedtea6-plugin  Plus "icedtea-6-plugin" are listed as the downloads.

Suggestions on where to go from here?  Can I remove those 3 and continue operations long enough to try installing again? How important are they to  java and does update manager use jave?

TIA
Dave

PS
From a terminal screen would that command be:
```
sudo apt-get remove icedtea6-plugin icedtea-netx icedtea-plugin
```

---

### Post by Cheesemill on 2012-07-13
It's probably a good idea to remove all of the version 6 plugins and then install the new version 7 ones instead.

Java v6 has security issues that have only been fixed in the new version 7.

---

### Post by Silvernail on 2012-07-13
> **Cheesemill said:**
> It's probably a good idea to remove all of the version 6 plugins and then install the new version 7 ones instead.

Java v6 has security issues that have only been fixed in the new version 7.
Do I use ```
sudo apt-get remove icedtea6-plugin icedtea-netx icedtea-plugin
```? Or will "icedtea6-plugin" be sufficient?

And what do I use to guarantee I get version 7?

Thanks for the feedback.
D

---

### Post by Silvernail on 2012-07-14
Click on notafication icon in top panel does nothing.
Click on applications > other > Synaptic manager does nothing.
From commnad line ```
 synaptic-pkexec
```

Edit > Fix Broken Packages produces this error: > E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

The above happens when I try to remove 'opendjk-6-jre-headless'.
Exit from program back into terminal.
dave@dave:~$ synapTic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: Dave Kelly,,, (dave)
Password: 
==== AUTHENTICATION COMPLETE ===
Discarding: 8 over 9
Discarding: 4 over 9

(synaptic:3632): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(synaptic:3632): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
dave@dave:~$ 

How can I fix broken dependies if it won't let me?
Is there some brute force way to remove version 6 of 'icedtea' and 'openjdk'?

Tia
D

---

### Post by Silvernail on 2012-07-14
I finally got all icedtea-6 plugins and stuff remover via 'synaptic'.

I have opendjk-7 installed. Do not see any plugins for version 7.

[SIZE="4"]?????[/SIZE]

The clinging icon in the panel is gone.

---

### Post by Silvernail on 2012-07-15
I'm do not know what I did different but evidently I screwed up and did the correct thing in the correct order.

Jave plugins version 6 is now gone. And what ever was supposed to be installed to replace it is now installed.

Mark Solved.

---

