---
title: "Firefox not working 11.10"
date: 2012-04-29
forum: General Help
---

### Post by gandalf3 on 2012-04-29
i went to open Firefox one day, and all i got was an error message:
"Firefox has encountered a problem and crashed please send an error report by checking box etc. etc." i wasn't to surprised, because i had probably more tabs open than i should have.. (probably over 40)
i sent the error report after several more tries including removing it in the software center, and installing again.
no dice.
i don't really like chrome, and i would like my firefox back:(

any help appreciated..

---

### Post by Frogs Hair on 2012-04-29
You may be having add-on trouble and you can start in safe mode from the terminal disable the add-ons. Then close safe mode and try to start normally.This will tell if it is an add-on causing the problem.```
firefox -safe-mode
```

---

### Post by gandalf3 on 2012-04-30
thanks.. but no go..

firefox -safe-mode
```
(firefox:2358): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:2358): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:2358): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(firefox:2358): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:2376): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:2376): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:2376): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(crashreporter:2376): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

just opens the error reporter again..

---

### Post by gandalf3 on 2012-05-05
is there anyway to get Firefox working again?
i would have thought a fresh install would do it..
maybe if i install it not from the software center? (synaptic or from Mozilla's website?) would this help?
BUMP..
any help appreciated.. :confused:

---

### Post by gandalf3 on 2012-05-24
well, after trying just about everything.. i tried to open a XML file, (which was defaulted to open with Firefox)
and it opened! :) no idea why now.. and the little white arrow next to the fire fox icon that says you have an instance open, is not there..

---

### Post by holycow131415 on 2012-05-25
did you try googling the error? i found this in 2 seconds...

[http://ubuntutechnical.wordpress.com/2011/11/07/gtk-warning-unable-to-locate-theme-engine-in-module_path-pixmap/](http://ubuntutechnical.wordpress.com/2011/11/07/gtk-warning-unable-to-locate-theme-engine-in-module_path-pixmap/)

---

### Post by gandalf3 on 2012-05-25
yes i did.. but not very well, it seems.. (never saw anything like that)
oh well..
it works now (complete with white arrow which started working after i rebooted) and i don't *think* i installed the  gtk2-engines-pixbuf thing.. 
but thanks all the same!:)

---

### Post by legendbb on 2012-08-31
That's exact the answer I have been looking for, thanks to holycow131415

---

