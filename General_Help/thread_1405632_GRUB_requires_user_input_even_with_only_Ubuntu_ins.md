---
title: "GRUB requires user input even with only Ubuntu installed"
date: 2010-02-12
forum: General Help
---

### Post by MockY on 2010-02-12
GRUB on the install of 9.10 on my mediacenter is acting odd. The only OS installed is Ubuntu, so the selection screen should not even show. However, it forces me to select Ubuntu or Memory test, and that without a counter. Since the mediacenter is headless (obviously since it's a mediacenter), I don't have a keyboard attached to it, hence, Ubuntu will not boot until I select it.

Why is this and how do I fix it? I have noticed that this happens randomly on other machines with 9.10 as well, but those are Desktops, so selecting Ubuntu from the Grub menu is not that big of a deal. But on the mediacenter it is.

---

### Post by golanbatrac on 2010-02-12
Open the config file for grub:

```
sudo nano /etc/default/grub
```

Post the contents of the file.

---

