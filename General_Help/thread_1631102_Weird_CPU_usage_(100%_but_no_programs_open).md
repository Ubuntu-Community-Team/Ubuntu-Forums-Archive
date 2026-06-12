---
title: "Weird CPU usage (100% but no programs open)"
date: 2010-11-26
forum: General Help
---

### Post by Biopyro on 2010-11-26
I have no idea what's happening here. The PC does not seem louder, and programs appear to run normally, but CPU usage is registered as very high all the time. It doesn't drop below the levels shown in the screen shot. What could be happening?
[IMG]http://img695.imageshack.us/img695/4629/programlist.png[/IMG]
[IMG]http://img819.imageshack.us/img819/3668/cpuk.png[/IMG]

---

### Post by dino99 on 2010-11-26
are you using boinc or like ?

sudo dpkg-reconfigure -phigh -a

have you found some usefull errors logged ? Watch .xsession-errors (/home, ctrl+h to unhide it) and into : system admin logviewer

---

### Post by Biopyro on 2010-11-26
Terminal command output
> name@name-desktop:~$ sudo dpkg-reconfigure -phigh -a
[sudo] password for guy: 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 6580
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.


I am running NOTHING, no BONIC, no modelling or anything similar

---

### Post by cottfcfan on 2010-11-26
Try typing "top" in a terminal and see if that shows whats eating your cpu.

---

### Post by dino99 on 2010-11-26
so goto synaptic and remove/purge ALL the flash related installed packages

then check that "canonical partner" repo is enabled into: synaptic repo tab (third party)

then install flashplugin-installer

---

### Post by Biopyro on 2010-11-26
typing top gives me this output. I'll try the flash stuff and report back. EDIT:adobeflashplugin is the only one, and removing via synaptics gives me this > E: adobe-flashplugin: subprocess installed pre-removal script returned error exit status 2
[IMG]http://img502.imageshack.us/img502/1732/pcload.png[/IMG]

---

### Post by Jouke74 on 2010-11-26
Ok, "HP" is eating up all your CPU time, but I don't know what it does.

---

### Post by Biopyro on 2010-11-26
How utterly bizzare. I don't know exactly when, but sometime after that post my cpu dropped to normal. Flash stopped working, so I restarted and when prompted by firefox to "install missing plugins" I did, and after restarting firefox everything went back to normal. 

Trying to install flash from abobe's page was totally unsuccessful, so I assume flash confused package manager somewhat too. Thanks for your help!

---

