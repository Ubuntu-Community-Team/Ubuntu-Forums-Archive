---
title: "I removed my administration abilities."
date: 2010-02-01
forum: General Help
---

### Post by Barashkukor on 2010-02-01
After installing Ubuntu 9.10 on a public access computer, I went in and set a sudo password and then removed administration abilities from the only current user.  Now I can't change any settings.  I have no idea how to fix this.  I am still kind of new to Ubuntu so this may be really easy to fix, please help!

---

### Post by lykwydchykyn on 2010-02-01
> **Barashkukor said:**
> After installing Ubuntu 9.10 on a public access computer, I went in and set a sudo password and then removed administration abilities from the only current user.  Now I can't change any settings.  I have no idea how to fix this.  I am still kind of new to Ubuntu so this may be really easy to fix, please help!

If you want to restore admin privileges to the user:
 - Reboot
 - Hit "esc" when prompted to access the GRUB menu
 - Select "root shell" from the menu
 - Enter the following command:
```

usermod -a -G admin someuser

```
where 'someuser' is the username of the account.

Then type "exit" and select "continue" from the menu.

---

### Post by Barashkukor on 2010-02-01
Thank you much, I'll try that.

---

### Post by Barashkukor on 2010-02-01
For some reason when I started it up there was no prompt to access the GRUB menu.

---

### Post by Leppie on 2010-02-01
> **Barashkukor said:**
> For some reason when I started it up there was no prompt to access the GRUB menu.
in karmic (9.10) it's SHIFT instead of ESC.
select a recovery mode, or press "e" to edit the boot parameters, scroll to the end of line with "quiet splash" and add "s" at the end, then press CTRL+x to boot.

---

### Post by lykwydchykyn on 2010-02-01
> **Barashkukor said:**
> For some reason when I started it up there was no prompt to access the GRUB menu.

Hit 'esc' repeatedly as it boots, and you should get a menu.  Don't hit it too much or you'll cause a keyboard fault.  About one keystroke/second usually does the trick.

EDIT: oops, leppie corrected me.  It's "SHIFT" now.  sorry.

---

