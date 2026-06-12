---
title: "Cant run any program after ubuntu update"
date: 2009-12-28
forum: General Help
---

### Post by panaeolus on 2009-12-28
hi im new to ubuntu
i make an update to my server,but after that i get 
a bunch of errors .....
failed to load hal(i manage to bybass it ,but return back
try to uninstall wine 
but after that when asks me for admin password ,icant write anythink in terminal window 
:guitar:

---

### Post by gradinaruvasile on 2009-12-28
The password is not shown - not even asterisks/dots - when typing it in terminal.

---

### Post by Earl_Maroon on 2009-12-28
Have you tried the consoles by pressing ctrl+alt+f1 (or f2,f3,f4,f5,f6)?
They're very handy if X is giving problems.
ctrl+alt+f7 takes you back to X.

---

### Post by panaeolus on 2009-12-28
* Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Setting up libaudio2 (1.9.1-1) ...

Setting up wine (1.1.35~winehq0~ubuntu~8.04-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 acpid
 acpi-support
E: Sub-process /usr/bin/dpkg returned an error code (1)


all my programs utorrent etc loading but close after few secs
only mozilla works

i use autoremove wine and install it again
but seems to fail load any aplication

---

### Post by panaeolus on 2009-12-29
try to run mtorrent via terminal 
thats the error
wine client error:0: version mismatch 381/394.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

---

### Post by panaeolus on 2009-12-29
any suggestions? :confused:

---

### Post by panaeolus on 2009-12-29
well i do

sudo aptitude purge acpid 

manage to uninstall acpid,but then when try to install it again  error occured

acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1

---

