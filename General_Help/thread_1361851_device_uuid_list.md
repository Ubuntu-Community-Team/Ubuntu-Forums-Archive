---
title: "device uuid list ?"
date: 2009-12-22
forum: General Help
---

### Post by MrPage on 2009-12-22
is there a way or command to list the uuid tags for all of the devices on my computer?

googling this only turns up how to see the uuids for harddrives and partitions - not useful...

I was really hoping to see a command like lspci that displayed this information.

does anyone know of such a critter?

---

### Post by audiomick on 2009-12-22
wouldn't mind knowing that myself...:)

---

### Post by rnerwein on 2009-12-22
just type: sudo blkid -c /dev/null
where /dev/null means - don't use the cache
ciao
  richi

---

### Post by audiomick on 2009-12-22
Thank you very much!

---

### Post by MrPage on 2010-01-01
well no, that command just displays the uuids of the drives and partitions...  not all of the devices on the system.

---

### Post by ibuclaw on 2010-01-01
When you say UUID - do you really mean the Manufacturer and Device ID's instead?

---

### Post by MrPage on 2010-01-02
yes, exactly.

as in here:
[http://en.wikipedia.org/wiki/Universally_Unique_Identifier](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)

---

### Post by ibuclaw on 2010-01-05
Well - not sure any other device has a UUID to tie it to the specific device in Linux (seems like it is only done for File Systems).

You can - however search for all device information using udevadm.

```
sudo udevadm info -a -p $(udevadm info -q path -n **/dev/sda**)
```

The last bit being the path of the device in /dev that you want to search up.

Regards
Iain

---

