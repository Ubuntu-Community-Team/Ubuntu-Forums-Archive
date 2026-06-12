---
title: "Enabling GRUB splash screen with 1 OS Install only ?"
date: 2010-09-28
forum: General Help
---

### Post by MindCalamity on 2010-09-28
How do I do that ? Currently I have Kubuntu/Mint KDE installed as my main and only OS so the GRUB splash is disabled by default, how do I enable that (so I'm able to change the boot commands to go to single user mode).?

---

### Post by drs305 on 2010-09-28
I think what you are really asking is how to display the Grub2 menu at startup, since the default for a single OS is *not* to show the menu.

If that is the case, open /etc/default/grub as root and comment out a line:

Open /etc/default/grub for editing as root:
```
gksudo gedit /etc/default/grub
```

Add a # symbol at the start of this line:
> GRUB_HIDDEN_TIMEOUT=0
To:
> **[COLOR="DarkRed"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0

The menu should display for the value in "GRUB_TIMEOUT=".
Save the file, then update-grub:
```
sudo update-grub
```

---

### Post by MindCalamity on 2010-09-28
> **drs305 said:**
> I think what you are really asking is how to display the Grub2 menu at startup, since the default for a single OS is *not* to show the menu.

If that is the case, open /etc/default/grub as root and comment out a line:

Open /etc/default/grub for editing as root:
```
gksudo gedit /etc/default/grub
```Add a # symbol at the start of this line:

To:


The menu should display for the value in "GRUB_TIMEOUT=".
Save the file, then update-grub:
```
sudo update-grub
```

Thread solved, thanks !

---

