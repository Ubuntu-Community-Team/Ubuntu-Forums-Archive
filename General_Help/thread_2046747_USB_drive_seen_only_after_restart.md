---
title: "USB drive seen only after restart"
date: 2012-08-23
forum: General Help
---

### Post by aerokamesh on 2012-08-23
Newbie alert.

I just installed 11.10 (3.0.0-12-generic) on a Dell Precision 390 (Pentium 4).

I noted that the USB flash drives are recognized and the contents shown only after a restart. When I eject and re-insert, nothing happens.

USB mouse doesnt work either (with restart or without).

Google only gave me a myriad of trial error solutions one of them being, "acpi=force irqpoll" in grub that seems to have worked for somebody. Other options included playing with the modules etc. Nothing worked for me. 

any help is greatly appreciated.

---

### Post by Marqin on 2012-08-23
Plug out your device.
```

cd /dev
ls

```
Then plug in it, a do:
```
ls
```
If something new like "sdc1" or "sdd1" appeared do:
```

sudo mkdir /mnt/my_disc
sudo mount /dev/this_new_thing_that_appeared /mnt/my_disc
```

---

### Post by aerokamesh on 2012-08-23
> **Marqin said:**
> Plug out your device.
```

cd /dev
ls

```Then plug in it, a do:
```
ls
```If something new like "sdc1" or "sdd1" appeared do:
```

sudo mkdir /mnt/my_disc
sudo mount /dev/this_new_thing_that_appeared /mnt/my_disc
```

There was no "sdb1", "sdc1" or "sdd1"

---

