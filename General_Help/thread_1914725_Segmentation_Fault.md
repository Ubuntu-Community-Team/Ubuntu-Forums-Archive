---
title: "Segmentation Fault"
date: 2012-01-24
forum: General Help
---

### Post by konts_A on 2012-01-24
I use ubuntu 11.04. After the upgrade. 
When I use Eclipse Indigo. Eclipse crash with error Segmentation fault.
Eclipse worked without errors for six months. This is not the fault of Eclipse.How can I find out why this was happening?

---

### Post by bluexrider on 2012-01-24
open a terminal and use the command to start Eclipse Indigo, this will give you the error code

---

### Post by konts_A on 2012-01-25
I run eclipse
 -console -consoleLog -debug -vmargs -Xmx384M

I see when crash:

>  ** (Eclipse:15173): DEBUG: NP_Initialize
 ** (Eclipse:15173): DEBUG: NP_Initialize succeeded
** No bp log location saved, using default.**
 [000:000] Browser XEmbed support present: 1
 [000:000] Browser toolkit is Gtk2.
 [000:000] Using Gtk2 toolkit
 [000:000] Warning(optionsfile.cc:47): Load: Could not open file, err=2
 [000:000] No bp log location saved, using default.
 [000:001] Browser XEmbed support present: 1
 [000:001] Browser toolkit is Gtk2.
 [000:001] Using Gtk2 toolkit
 ** (Eclipse:15173): DEBUG: NP_Initialize
 ** (Eclipse:15173): DEBUG: NP_Initialize succeeded
 ** (Eclipse:15173): DEBUG: NP_Initialize
 ** (Eclipse:15173): DEBUG: NP_Initialize succeeded
 ** (Eclipse:15173): DEBUG: NP_Initialize
 ** (Eclipse:15173): DEBUG: NP_Initialize succeeded
** Segmentation fault**


Where can I fine **default** log

---

### Post by bluexrider on 2012-01-25
Check your /var/log

Thats where the default logs are

---

### Post by konts_A on 2012-01-25
~$ /home/konst/bin/eclipse/indigo/eclipse
> ** (Eclipse:10859): DEBUG: NP_Initialize
** (Eclipse:10859): DEBUG: NP_Initialize succeeded
No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
[000:001] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:001] No bp log location saved, using default.
[000:001] Browser XEmbed support present: 1
[000:001] Browser toolkit is Gtk2.
[000:001] Using Gtk2 toolkit
** (Eclipse:10859): DEBUG: NP_Initialize
** (Eclipse:10859): DEBUG: NP_Initialize succeeded
** (Eclipse:10859): DEBUG: NP_Initialize
** (Eclipse:10859): DEBUG: NP_Initialize succeeded
** (Eclipse:10859): DEBUG: NP_Initialize
** (Eclipse:10859): DEBUG: NP_Initialize succeeded
Segmentation Fault

syslog:
Jan 26 11:39:01 bor CRON[11006]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
I no longer see the files (in /var/log) that have changed at this time (Jan 26 11:39)
When I debug a PHP and Eclipse crash.

---

### Post by vekinn on 2012-01-26
Try forcing mozilla, I believe webkit-gtk is causing the segfault.
./eclipse -vmargs -Dorg.eclipse.swt.browser.DefaultType=mozilla

---

### Post by konts_A on 2012-01-27
**Thank you! **
With this option Eclipse not crash.

---

