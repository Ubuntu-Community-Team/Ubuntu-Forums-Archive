---
title: "Ubuntu One asks for permission at start up"
date: 2010-11-30
forum: General Help
---

### Post by Shii on 2010-11-30
I get two password manager requests from Ubuntu One every time I boot. Is there a way to stop them from showing up?

---

### Post by Shii on 2010-12-02
Bump, I can't be the only one with this problem...

---

### Post by mister_playboy on 2010-12-02
System > Preferences > Passwords and Encryption Keys

If you expand the Passwords:login folder, Ubuntu One should be one of the listed apps.  You can modify the password there so it matches your current login password.

See if that solves your problem.

---

### Post by Shii on 2010-12-02
Interesting... when I open that window, both folders are empty. I logged into Ubuntu One manually and it showed up in the Default folder, but I can't change the password there.

---

### Post by mister_playboy on 2010-12-02
Next thing to try is to go into your ~/.gnome2/keyrings folder and delete the files there.

Logout and back in, you should be asked to enter your password so your keyrings can be rebuilt.  Hopefully the password prompts will stop after that... if not, some else will have to help you. ;)

---

