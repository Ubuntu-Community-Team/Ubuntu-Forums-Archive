---
title: "Grub Display Upon Boot."
date: 2010-01-08
forum: General Help
---

### Post by Tayl on 2010-01-08
Hello all.

Just a quickie for you all. How do I get Grub to actually display as opposed to automatically choosing which OS to boot and booting it?

Regards,

Tayl.

---

### Post by mk1w86 on 2010-01-08
Run

```
sudo gedit /etc/default/grub
```

and comment out 

GRUB_HIDDEN_TIMEOUT=0

then run

```
sudo update-grub
```

---

### Post by Leppie on 2010-01-08
if you're using grub2, just amend the following lines in your grub defaults file /etc/default/grub like this:
```
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
```

regenerate the grub.cfg file:
```
sudo update-grub
```

---

### Post by Tayl on 2010-01-08
Brilliant, thank you!

Tayl.

---

### Post by Leppie on 2010-01-08
you're welcome :)

---

