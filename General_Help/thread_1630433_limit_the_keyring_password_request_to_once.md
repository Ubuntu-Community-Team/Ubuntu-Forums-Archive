---
title: "limit the keyring password request to once"
date: 2010-11-25
forum: General Help
---

### Post by joselitux on 2010-11-25
Hi all

I know it's safer not to block the request for a password that unblocks the keyring but I'm desperate.
The more I use ubuntu more times I'm requested to provide the keyring password. Now, this time, i've typed 7 times!!!!!!


is there a way to limit this nighmare. Every time I bootup i got tired.

thankx in advance

---

### Post by JustinR on 2010-11-25
Hi,

If you change the keyring password (System > Applications > Passwords and Encryption Keys on Ubuntu Maverick Meerkat) to your login password, it should automatically unlock.

---

### Post by joselitux on 2010-11-25
I got no such menu (system - applications) in Maverick.
i got System > Preferences > Passwords and Encryption Keys, but I didn't got your point.
what do you mean by "change the keyring password"?

I assume the new password will be requested 7 times again because no config has made but a password change.

---

### Post by JustinR on 2010-11-25
> **joselitux said:**
> I got no such menu (system - applications) in Maverick.
i got System > Preferences > Passwords and Encryption Keys, but I didn't got your point.
what do you mean by "change the keyring password"?

I assume the new password will be requested 7 times again because no config has made but a password change.

Sorry about that - it's four in the morning where I'm at.

Its supposed to be 'System > Preferences > Passwords and Encryption Keys'.
Once you open the program, click on the keyring called 'Passwords: Default' and click 'Change Password'. Enter in the old password and for the new password type in your login password. Press 'Ok' or 'Apply' and restart your computer and it should stop asking you to unlock the keyring.
Good luck!

---

### Post by joselitux on 2010-11-25
No success. The new password is requested as much as the old one.

---

### Post by JustinR on 2010-11-25
> **joselitux said:**
> No success. The new password is requested as much as the old one.

Okay, can you go into the network manager, and whatever your default connection is, select it and press 'Edit', and click 'Available to All Users' and press 'OK/Apply' and restart your computer and see if that does anything.

If that doesn't fix the problem,
Can you post what you '/etc/pam.d/gdm' file looks like?

---

### Post by joselitux on 2010-11-25
I'm connected via LAN wire, so the wireless is not the problem.
The network manager option "available to all users" is checked, so no change is made. No rebooting needed.

My '/etc/pam.d/gdm' below:

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password
```

---

