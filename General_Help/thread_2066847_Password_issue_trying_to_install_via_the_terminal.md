---
title: "Password issue trying to install via the terminal"
date: 2012-10-05
forum: General Help
---

### Post by rmcellig on 2012-10-05
This must be my luck linux day because things are not going as normal with my Xubuntu install. ;)

When I try to install via the terminal, I get this:

randy is not in the sudoers file.  This incident will be reported.

I have no idea what this is or how to fix it. What should I do and what would cause this?

I am using Xubuntu 12.04

---

### Post by steeldriver on 2012-10-05
Is 'randy' the original user that you installed with? if not, then you can log in with that account (which will have 'sudo' permission by default) and either do the install as that user, or add 'randy' to the 'sudo' group from there

If 'randy' *was* your primary account, then somehow you have removed yourself from the 'sudo' group and will have to re-add yourself from the recovery console

```
gpasswd --add randy sudo
```

---

### Post by rmcellig on 2012-10-05
When I set up Xubuntu my initial user account was named home. This is set up on my text PC where I try out all sorts of things in Linux. What I did while in my home account was create a new user using the Users and Groups GUI, and called the new account randy with admin privileges. Both the home and randy accounts have admin priviliges.

---

### Post by rmcellig on 2012-10-05
Thanks! That worked

---

