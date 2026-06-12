---
title: "Bugs?"
date: 2011-06-29
forum: General Help
---

### Post by yelserpdog on 2011-06-29
I've noticed what I think are a couple of bugs in my installation (Narwal).

1. Every I boot up it, after I log and the desktop loads it asks me for a password to unlock my keyring. I have to enter this password at least 2 times before it accepts it. (yes I am definitely typing the right password in)

2. Every time I install something from the software centre it says the installation failed but it is actually installing the item.

Does anyone know what's going on here? They're not life or death problems but would stop annoying me if I could get rid of them. (Beware, noob alert!)

---

### Post by sanderd17 on 2011-06-29
> **yelserpdog said:**
> I've noticed what I think are a couple of bugs in my installation (Narwal).

1. Every I boot up it, after I log and the desktop loads it asks me for a password to unlock my keyring. I have to enter this password at least 2 times before it accepts it. (yes I am definitely typing the right password in)

try to go to the "users and group" settings (somewhere in a settings menu, I don't know what interface you use). And try if it works by setting "automatic login", logout and login and than revert to the normal.
> 

2. Every time I install something from the software centre it says the installation failed but it is actually installing the item.

Does anyone know what's going on here? They're not life or death problems but would stop annoying me if I could get rid of them. (Beware, noob alert!)

Can you try
```

sudo apt-get update
sudo apt-get upgrade

```

If you get errors, please tell them here. If you don't get errors, than the GUI of the software center has a problem.

---

### Post by yelserpdog on 2011-07-01
Thanks:

I can't find the setting to automatically login yet.

I used the code you said for the second problem and got the following error at the end:


DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by haqking on 2011-07-01
just set a blank password for your keyring in passwords and encryption keys (depending on your menus)

and as above for the apt-get update/upgrade etc

---

### Post by sanderd17 on 2011-07-02
> **yelserpdog said:**
> 

```

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

try

```

sudo dpkg --configure firmware-b23-lpphy-installer

```

you will probably get an error too, please tell it here.

---

