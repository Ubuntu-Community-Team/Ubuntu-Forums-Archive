---
title: "Install program hangs after &quot;Install Ubuntu Server&quot; is selected"
date: 2010-01-21
forum: General Help
---

### Post by intermentals on 2010-01-21
I have a compaq server machine (ProLiant DL380 G2) that I'm trying to install Ubuntu Server on at the moment

However when I select "Install Ubuntu Server" it hangs with a flashing cursor

At first it was displaying an error message:

"create_floppy_devices[195]: specified group 'floppy' unknown"

but then after I disabled the diskette boot option and the integrated diskette controller in the BIOS it has just started to hang with no on screen messages at all (this is true if one or the other of these options is enabled)

Really baffled! Please help

---

### Post by intermentals on 2010-01-21
incidentally a desktop disk I got with Ubuntu Unleashed works fine adding to my confusion

---

### Post by intermentals on 2010-01-21
after a while (180 seconds I guess) I get the error message:

"udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:000f.1/host0/target0:0:0/0:0:0:0/block/sr0 (933 [   181,434278] Kernel panic - not syncing: Attempted to kill init!"

---

### Post by intermentals on 2010-01-28
bump

---

### Post by dennymeta on 2010-05-24
I'm seeing what I think is the same problem with an Ubuntu Server 10.04 DVD downloaded yesterday...  first I get the floppy group error, then a long delay, then a bunch of kernel errors relating to '/devices/pci0000:00/...', sometimes finishing with a panic.

---

### Post by EA3BIL on 2011-01-25
Any reasons for this error to show up?

I'm trying to instal 10.04LTS Server on a DL380 G2 and I'm sick of this error message...

Any ideas will be useful!.

Thank you,
Rafa.

---

### Post by twocvbloke on 2011-03-23
Just thought I'd ask if anyone has a solution, I too have a Compaq DL380 G2 and it's doing exactly the same thing, I had used an older version CD the other night (v9.04), but that was too damaged to work properly, but that one worked fine up until it got to the damaged bits on the disc, but downloading v10.10nhas resulted in the symptoms already described here... :(

Any ideas? Is the Compaq DL380 G2 "too old" for modern Linux? And if so, what's the non-windows alternative?

---

