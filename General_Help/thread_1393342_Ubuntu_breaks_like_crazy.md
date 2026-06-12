---
title: "Ubuntu breaks like crazy"
date: 2010-01-29
forum: General Help
---

### Post by Lockheed on 2010-01-29
I left windows to find trouble-free environment but Ubuntu drives me up the wall every so often.

Here is the latest:
```
sudo apt-get purge blah_blah_blah
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

and

```
sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.33-rc5
Cannot find /lib/modules/2.6.33-rc5
update-initramfs: failed for /boot/initrd.img-2.6.33-rc5
dpkg: subprocess post-installation script returned error exit status 1
```

I might add that I am using 2.6.32 and 2.6.33-rc5 I removed after unsuccessful installation (yay - impossibility to install newest kernel - another cool Ubuntu feature).

---

### Post by c0mput3r_n3rD on 2010-01-29
Have you tried a "sudo apt-get update" and "sudo apt-get upgrade"?

---

### Post by Lockheed on 2010-01-29
> **c0mput3r_n3rD said:**
> Have you tried a "sudo apt-get update" and "sudo apt-get upgrade"?

Yes,
```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

and No.
Using sudo apt-get upgrade would spell disaster to my system.

---

### Post by Lockheed on 2010-01-30
Seriously, I need some help with this, urgently, as I cannot install/remove anything now.

---

### Post by Lockheed on 2010-02-01
removing a leftover custom kernel file from /var/lib/initramfs-tools solves the problem.

---

