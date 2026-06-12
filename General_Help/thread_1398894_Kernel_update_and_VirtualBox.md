---
title: "Kernel update and VirtualBox"
date: 2010-02-05
forum: General Help
---

### Post by Fake51 on 2010-02-05
Just a quick hint for anyone in the same situation as me this morning: just updated the kernel image on my Ubuntu 9.10 install which led to VirtualBox violently refusing to run.

The fix for this is quite simple: reinstall the virtualbox-ose-source module. Consider doing a backup of your VMs first, though, for good measure. After that, this should do the trick (if you installed through apt in the first place):

```
sudo apt-get autoremove virtualbox-ose-source
sudo apt-get install virtualbox-ose-source

```
This will rebuild the module that VirtualBox depends on to run.

---

### Post by Bachstelze on 2010-02-05
```
/etc/init.d/virtualbox-ose setup
```

No need to reinstall. :)

---

### Post by lotharmat on 2010-02-05
> **Bachstelze said:**
> ```
/etc/init.d/virtualbox-ose setup
```

No need to reinstall. :)

Mine worked straight after the new Kernel install.

---

### Post by Fake51 on 2010-02-05
> **Bachstelze said:**
> ```
/etc/init.d/virtualbox-ose setup
```

No need to reinstall. :)

Had no luck with that, I'm afraid, hence the reinstall.

---

### Post by Uncle Spellbinder on 2010-02-05
No issues here. Kernel updated, rebooted, started virtual box without issue.

---

### Post by SecretCode on 2010-02-05
Do you have dkms installed? Saves a lot of bother with kernel upgrades.

---

### Post by Uncle Spellbinder on 2010-02-05
> **SecretCode said:**
> Do you have dkms installed? Saves a lot of bother with kernel upgrades.

Indeed I do.

---

