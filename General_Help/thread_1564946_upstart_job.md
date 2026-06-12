---
title: "upstart job"
date: 2010-08-31
forum: General Help
---

### Post by xiaoyafeng on 2010-08-31
I'm tired to input modprobe blah blah for running Virtual Box.
and write a upstart job for doing this but doesn't work:
Below is the content in remove-kvm.conf:


description	"close kvm-intel"

start on  started dbus

respawn

exec /sbin/modprobe -r kvm-intel 


here is the output of initctl list:
dmesg stop/waiting
kvm-delete stop/waiting
network-interface-security start/running
networking stop/waiting
procps stop/waiting
tty6 start/running, process 1714
ureadahead stop/waiting


what I confused are it works well when I manually input start remove-kvm.


Help!

---

