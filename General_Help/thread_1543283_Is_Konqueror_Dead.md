---
title: "Is Konqueror Dead?"
date: 2010-07-31
forum: General Help
---

### Post by tdr2009 on 2010-07-31
I've been wondering, is Konqueror dead? I see it can't display a number of sites correctly, e.g. ubuntuforums.org, youtube.com, etc. 
So, is it dead, or is there going to be improvements on KHTML? I know it needs it.

---

### Post by NightwishFan on 2010-07-31
I am sure the project is still working, it had it's last stable release 30 days ago. Though if you want better compliance, I believe you can experimentally run Konqueror using Webkit.

It is a pity if it is phased out, it was my favorite Web Browser for a long time until I found Epiphany.

---

### Post by jerenept on 2010-07-31
IN B4 recurring.

Konqueror is Awesome!

---

### Post by tdr2009 on 2010-07-31
> **NightwishFan said:**
> I am sure the project is still working, it had it's last stable release 30 days ago. Though if you want better compliance, I believe you can experimentally run Konqueror using Webkit.

It is a pity if it is phased out, it was my favorite Web Browser for a long time until I found Epiphany.

Whenever i use anything with webkit, it crashes. For instance when I use rekonq, or Arora, it crashes loading a webpage, on xfce and kde. They both use webkit. I tried it on Konqueror, and it did the exact same thing, it loaded simple webpages, like google. but if i try acid3 test, it crashes, or if i try youtube. Should i report it as a bug, or reinstall webkit somehow?

---

### Post by NightwishFan on 2010-07-31
Here is some information on reporting bugs. If it is crashing uncommonly perhaps you should report one.
[https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting](https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting)

If you have any more specific information I will try to go on it.

---

### Post by tdr2009 on 2010-08-01
> **NightwishFan said:**
> Here is some information on reporting bugs. If it is crashing uncommonly perhaps you should report one.
[https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting](https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting)

If you have any more specific information I will try to go on it.

I ran **Arora** from terminal, and got these errors: 
(process:3035): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:3035): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3035): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault
[B]

and Konqueror:[/B]
konqueror(3067)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/kwebkitpart.so" does not offer a qt_plugin_instance function.

(process:3067): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:3067): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3067): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
KCrash: Application 'konqueror' crashing...
sock_file=/home/travis/.kde/socket-ubuntu/kdeinit4__0

[1]+  Stopped                 konqueror
[B]

and Rekonq:[/B]
rekonq(3165)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:

(process:3165): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:3165): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:3165): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
KCrash: Application 'rekonq' crashing...
sock_file=/home/travis/.kde/socket-ubuntu/kdeinit4__0





those are all webkit applications i have, firefox works just fine.

---

### Post by giddyup306 on 2010-08-01
> **jerenept said:**
> 

Konqueror is Awesome!

At crashing.

---

### Post by NightwishFan on 2010-08-01
I am sorry to say I am not a coder, and do not really understand that output. I was hoping there would be something more clear. Do they crash so often they are unusable or can you reproduce a specific crash. If so, you need to file the bug report yourself so apport can automatically attach debugging information from your system.

I hope I can be of help and I will try to answer any questions.

---

### Post by Dustin2128 on 2010-08-01
should be in community cafe, in recurring :D. Anyway seeing as konqueror has half of a quarter of a percent of the market share, nobody develops for it, and its not standards compliant enough for my tastes anyway.

---

