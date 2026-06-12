---
title: "What happened to the Device Manger?"
date: 2011-11-01
forum: General Help
---

### Post by lampak on 2011-11-01
I've reinstalled Ubuntu some time ago and was going to reinstall the Device Manager as well (the gnome-device-manager package). It turns out, however, that it was removed from the repository! 

Which makes me ask a couple of questions:
1) WHY?! 
2) Has it been replaced by other app with the same or greater functionality? Do you know one?
3) Is it available in a PPA of something?

Everything I've managed to google was [this reason for deletion by Martin Pitt](https://launchpad.net/ubuntu/oneiric/amd64/gnome-device-manager):
> 
obsolete, hal GUI


edit: Because I haven't made it clear: I'm using Ubuntu 11.10 "Oneiric Ocelot".

---

### Post by christopher.wortman on 2011-11-01
In software center enable extra software, it was moved since "nobody really uses it anymore" according to the developers. One more annoyance I suppose.

---

### Post by lampak on 2011-11-01
> **christopher.wortman said:**
> In software center enable extra software,
I've got the "universe" and all the rest enabled in Software Sources, if that's what you mean. Still no device manager in sight.

> **christopher.wortman said:**
> it was moved since "nobody really uses it anymore" according to the developers. One more annoyance I suppose.
Yeah, because an average bread-eater had all the >50k packages from the repo installed except for this one, so they've removed it since it was the least used one.

edit: Sorry, I've misread "moved" as "removed". But it still seems to have been the latter.

---

### Post by christopher.wortman on 2011-11-01
It is in the Universe.

[http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-device-manager/](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-device-manager/)

You have to enable universe to get updates or simply download the deb from this site.

---

### Post by crdlb on 2011-11-01
> **lampak said:**
> I've reinstalled Ubuntu some time ago and was going to reinstall the Device Manager as well (the gnome-device-manager package). It turns out, however, that it was removed from the repository! 


It has indeed been remvoed from Oneiric: [https://launchpad.net/ubuntu/+source/gnome-device-manager](https://launchpad.net/ubuntu/+source/gnome-device-manager)

What exactly did you use it for? There is ["Disk Utility"]("apt:gnome-disk-utility") (palimpsest) and ["HardInfo"]("apt:hardinfo").

---

### Post by lampak on 2011-12-17
Simply to view information about the devices I've got installed. Sorry for not replying for so long, I can't even remember now what was the thing I needed it for then, but now I need to check what exactly the model of my WiFi card is - and since Ubuntu doesn't ship with a device manager of any kind (!) and it was the only one I knew, I'm left without a tool for this embarrassingly simple task. 

The apps you mentioned seem to be only for HDDs. Any ideas for a more universal replacement?

---

### Post by Paqman on 2011-12-17
[Hardinfo]("apt:hardinfo") and [Sysinfo]("apt:sysinfo") will both give you plenty of hardware information.

---

### Post by JC Cheloven on 2011-12-17
> **lampak said:**
> Simply to view information about the devices I've got installed.(...)
The apps you mentioned seem to be only for HDDs. Any ideas for a more universal replacement?
Perhaps this? ```
lshw
```
Note: hardinfo is also good as mentioned. It appears as "system profiler and benmarch" in my menu.

---

### Post by fragos on 2011-12-18
Install "Disk Utility" from the software center. It does everything I can think of plus a few -- very complete.

---

