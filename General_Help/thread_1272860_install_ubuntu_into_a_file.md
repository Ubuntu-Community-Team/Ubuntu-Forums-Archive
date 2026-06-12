---
title: "install ubuntu into a file"
date: 2009-09-22
forum: General Help
---

### Post by sea_monkey987 on 2009-09-22
i'm trying to install ubuntu onto my flash drive into a file on my fat32 partition.  wait.  don't laugh yet.  this actually makes sense. you know how linux allows you to create files as containers to hold whole partitions?  this is also how wubi works.  they say on their page that ubuntu is installed  into a file and then booted because the kernel mounts the installation via the loopback device.  i'm trying to do this on the flash drive.

i know there are tons of install to flash drive tutorials but they all require creating a separate partition to hold the ubuntu install. then you have to create another partition to hold any "persistent" updates.

---

### Post by mac9416 on 2009-09-22
There is [UNetbootin]("http://unetbootin.sourceforge.net/"), but it doesn't allow file persistence as far as I know. The other option is [Ubuntu live USB creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator").

Neither of those install into a single file, but they don't require a separate partition either.

Hope that helps.
-mac

---

### Post by sea_monkey987 on 2009-09-22
ok.  thanks.  i'll look into those if this completely fails...

i've made some progress though. i *think* i've successfully installed ubuntu into a file mounted and formated as an ext3 filesystem.  the  only thing now i need to do is figure out how to mount this filesystem at boot time as '/'.  i know i'm going to be using casper somehow.  but beyond that i'm lost.  can anybody help?

if this works out, i'll post complete instructions for others.  for now, it's just trial and error.

---

### Post by sea_monkey987 on 2009-09-23
bump?

---

