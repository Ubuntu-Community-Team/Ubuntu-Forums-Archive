---
title: "E: dpkg was interrupted"
date: 2009-11-21
forum: General Help
---

### Post by luctor on 2009-11-21
I've compiled my own kernel following the master kernel thread, [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158).
I was trying to include a kernel module for an unsupported webcam.

I wasn't happy with it so I removed the linux image and headers through synaptic.

All seemed ok but now I'm getting this error.
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

running the command in a terminal I get this
```
$ sudo dpkg --configure -a
Instellen van initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31.4-mk
Cannot find /lib/modules/2.6.31.4-mk
update-initramfs: failed for /boot/initrd.img-2.6.31.4-mk
dpkg: subproces installed post-installation script gaf een foutwaarde 1 terug
```

How do I fix this or how can I tell initramfs-tools not to update 2.6.31.4-mk ?

[SIZE="5"]**SOLVED = SOLVED = SOLVED = SOLVED = SOLVED = SOLVED = SOLVED = SOLVED = SOLVED = SOLVED **[/SIZE]

Removed /var/lib/dpkg/triggers/update-initramfs
ran dkpg --configure -a one more time
```

dkpg --configure -a
Instellen van initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)
```

Now every thing is fine ...

---

### Post by Rockanium on 2009-11-21
```
sudo dpkg --configure -a
```

---

### Post by 3rdalbum on 2009-11-21
```
sudo dpkg --audit
```

may give you more information on exactly what needs to be done.

---

### Post by luctor on 2009-11-21
> **Rockanium said:**
> ```
sudo dpkg --configure -a
```

As shown in the original post, that doesn't help ..

But thanks for answering anyway

---

### Post by NoaHall on 2009-11-21
Hm. Try opening Synaptic and locking the version. That will stop it trying to update, anyway.

---

### Post by luctor on 2009-11-21
> **NoaHall said:**
> Hm. Try opening Synaptic and locking the version. That will stop it trying to update, anyway.

Can't launch synaptic , that's gives the error mentioned in the original post ..

---

### Post by luctor on 2009-11-21
> **3rdalbum said:**
> ```
sudo dpkg --audit
```

may give you more information on exactly what needs to be done.

```
sudo dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs
```

and 
```
sudo dpkg --configure initramfs-tools
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31.4-mk
Cannot find /lib/modules/2.6.31.4-mk
update-initramfs: failed for /boot/initrd.img-2.6.31.4-mk
dpkg: subprocess installed post-installation script returned error exit status 1

```

Seems like a full circle
I need to remove 2.6.31.4-mk from update-initramfs .. but how ?

```
sudo update-initramfs -d -k "2.6.31.4-mk"
Cannot delete /boot/initrd.img-2.6.31.4-mk, doesn't exist.
```

---

### Post by NoaHall on 2009-11-21
Hm. I would say trying to force it, but that could cause damage.

dpkg --force-all --configure initramfs-tools

If you want to try it.

---

### Post by luctor on 2009-11-21
Its solved .

see top post

---

