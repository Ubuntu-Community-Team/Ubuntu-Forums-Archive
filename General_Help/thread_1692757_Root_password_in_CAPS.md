---
title: "Root password in CAPS"
date: 2011-02-21
forum: General Help
---

### Post by redheeler on 2011-02-21
I had the CAPS Lock on accidentally during my Ubuntu installation, when I entered in the root password it was with CAPS.

Now I am stuck having to hit the CAPS lock back and forth for password entry to perform various sudo tasks.

I have tried several methods below:

(not my real password)

:( Current password in CAPS: 2HOTDOGS

:) Desired password: 2hotdogs

```
sudo -i

sudo passwd root

sudo passwd
```None of these things worked.

It asks for the current password, and then new password, says it was changed successfully but when I reboot the old CAPS password remains.

Any help appreciated.

---

### Post by srs5694 on 2011-02-21
Ubuntu doesn't ask for the root password during installation. I suspect you entered your *user* password with the caps lock key active. To change your user password, you can use the passwd command *without* using sudo. There's also a GUI way to do it, but I don't recall the exact menu sequence (and my Ubuntu desktop system is currently booted into OS X, so I can't check that detail).

---

### Post by CharlesA on 2011-02-21
If you are using sudo, you aren't on the root account. Anyhow, you can change your *user* password from System > Preferences> About Me

---

### Post by redheeler on 2011-02-21
> **srs5694 said:**
> Ubuntu doesn't ask for the root password during installation. I suspect you entered your *user* password with the caps lock key active. To change your user password, you can use the passwd command *without*  using sudo. There's also a GUI way to do it, but I don't recall the  exact menu sequence (and my Ubuntu desktop system is currently booted  into OS X, so I can't check that detail).

> **CharlesA said:**
> If you are using sudo, you aren't on the root account. Anyhow, you can change your *user* password from System > Preferences> About Me

Thanks for the help - got it changed!  :KS

---

