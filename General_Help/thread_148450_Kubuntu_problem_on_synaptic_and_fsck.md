---
title: "Kubuntu problem on synaptic and fsck"
date: 2006-03-22
forum: General Help
---

### Post by wizzkid on 2006-03-22
Hi! I tried to lunch the synaptic, after entering the password, nothing happends, same thing with adept.  But when I tried to lunch it via terminal/ konsol sudo synaptic, it starts but prints this message on konsol

wizzkid@:~$ sudo synaptic
sudo: unable to lookup  via gethostbyname()
Password:

(synaptic:8515): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8515): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
wizzkid@:~$

what's the error unable to lookup via gethostbyname?

About the fsck. I tried to run sudo touch /forcefsck, after reboot, it does not check or scan my drive, its just a normal boot.

Btw, I set the password for su. im not sure if it has something to do with it,

Thanks. hope you could help!

---

