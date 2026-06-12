---
title: "Dual-boot issue"
date: 2011-05-20
forum: General Help
---

### Post by ManyBeers on 2011-05-20
My Gateway netbook dual-boots Vista Home @ 2Ubuntu 10.04. Until today that is. My setup uses Vistas bootloader to boot either Vista or Ubuntu. So grub is installed in sda3(Ubuntu root directory)and not MBR. I think an Ubuntu update messed Grub up.
Now when I select Ubuntu from my boot screen all I get is a flashing cursor in upper left corner. Windows boots fine.
I think I need to update Grub but I can't if Ubuntu won't load.
Using the SYSTEMRESCUECD with Gparted all my partitions show up
just fine. Any help would be apppreciated.
.

---

### Post by Hedgehog1 on 2011-05-20
Please use a LiveCD/LiveUSB with 10.10 (so you get the correct grub for you release).

Once you have boot and select 'TRY':

```
sudo mount /dev/sd**a3** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a3**
```

***The Hedge***

:KS

---

### Post by ManyBeers on 2011-05-20
> **Hedgehog1 said:**
> Please use a LiveCD/LiveUSB with 10.10 (so you get the correct grub for you release).

Once you have boot and select 'TRY':

```
sudo mount /dev/sd**a3** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a3**
```

***The Hedge***

:KS

Ok, will download iso. Sorry for the late response but I had business to attend to.

---

### Post by ManyBeers on 2011-05-20
> **Hedgehog1 said:**
> Please use a LiveCD/LiveUSB with 10.10 (so you get the correct grub for you release).

Once you have boot and select 'TRY':

```
sudo mount /dev/sd**a3** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a3**
```

***The Hedge***

:KS
Here is the result:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda3
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
```

---

### Post by linuxinstalledfromhdd on 2011-05-20
Okay now try this one:

[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by Hedgehog1 on 2011-05-20
Sorry - somehow I though you wanted it installed in sda3 - It didn't click that that was not where you wanted it installed.

**Here is the correct command for installing to the MBR:**

Please use a LiveCD/LiveUSB with 10.10 (so you get the correct grub for you release).

Once you have boot and select 'TRY':

```
sudo mount /dev/sd**a3** /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

---

