---
title: "Temporarily hide or disable user at login screen?"
date: 2010-05-08
forum: General Help
---

### Post by wisehumanity on 2010-05-08
Is there a way to temporarily hide or disable a user so that single user does not appear at the login screen on lucid. Then re-enable it at a later time should you so choose. Preferably I would just be able to hide the user from the login screen but still login to it by entering the user name manually.
Thanks.

---

### Post by aysiu on 2010-05-08
This guide is for 9.10, but I think 10.04 uses the same version of GDM:
[How to Remove (Hide) Users list at login Screen in Ubuntu 9.10 (Karmic)](http://www.ubuntugeek.com/how-to-remove-hide-users-list-at-login-screen-in-ubuntu-9-10-karmic.html)

---

### Post by StuartN on 2010-05-08
> **wisehumanity said:**
> Is there a way to temporarily hide or disable a user so that single user does not appear at the login screen on lucid.

I have not tried it (I disabled the list completely), but you would need to create or edit /etc/gdm/custom.conf according to the Greeter Options section of [http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en) by setting the include= or (better) the exclude= values.

---

