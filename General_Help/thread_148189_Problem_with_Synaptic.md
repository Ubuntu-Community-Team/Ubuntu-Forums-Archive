---
title: "Problem with Synaptic"
date: 2006-03-21
forum: General Help
---

### Post by Plexi on 2006-03-21
Hi, 

i'm a newbie with linux, installed ubuntu 5.10 just a few days ago. 

This is the scenario: 

I've just installed VPNC via Synaptic, started to set up VPNC in the terminal, then a minute or two later I want to check for something in Synaptic (I no longer remember what, 'cause I paniced when Synaptic failed to start, well, it doesn't matter now..). When clicking: System->Administration->Synaptic Package Manager, the symantic window pops up for a second or two, and then it's gone. I have rebooted, but the problem is still there..

I've tried "sudo synaptic" in the terminal. Then I get the message :

"(synaptic:9824): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9824): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault"

The same thing as above happens with the synaptic window, it pops up for a sec, then it's gone. 

Any suggestions?!

---

### Post by r4ik on 2006-03-21
Found this thread might be usefull,

[http://ubuntuforums.org/showthread.php?t=104906](http://ubuntuforums.org/showthread.php?t=104906)

Good luck !

---

### Post by Plexi on 2006-03-21
Thanks a lot!

The code "sudo rm /var/cache/apt/*.bin" made it work agan.

Again, thanks

---

### Post by r4ik on 2006-03-21
My pleasure enjoy Ubuntu.

---

