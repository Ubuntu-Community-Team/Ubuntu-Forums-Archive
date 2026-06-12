---
title: "Guest session, how to disable? ubuntu 9.04"
date: 2009-11-18
forum: General Help
---

### Post by kotelyan on 2009-11-18
I have made a special guest account for the guests to log in. How do I disable a Guest session ?

---

### Post by audiomick on 2009-11-18
Do you mean you want to know how to not be able to log-in as guest, or how to change users, or something else?

---

### Post by philinux on 2009-11-18
> **kotelyan said:**
> I have made a special guest account for the guests to log in. How do I disable a Guest session ?

[http://www.networkdictionary.com/software/Linux325.php](http://www.networkdictionary.com/software/Linux325.php)

---

### Post by kotelyan on 2009-11-18
No, I don't want to disable an account, that I created. What I am talking about is the following: - in the Gnome session there is a menu to shutdown/log out, etc... or switch to another user.
There is also an item "Guest" that switches to the session with minimal priviledges and no password. I checked the /etc/passwd, it seems  that it stands for the account with name guest, that has UID of 112, and does not show in the System Administration GUI.
Should I just comment out this line in the /etc/passwd, or is there a "nicer" way to get rid of it?

Thanks,

---

### Post by John Bean on 2009-11-18
Do you want to retain user switching at all? If not you can turn it off in the GNOME configuration under the /desktop/gnome/lockdown/disable_user_switching key.

Edit: I just found the key you want: /apps/fast-user-switch-applet/show_guest_login :-)

---

### Post by kotelyan on 2009-11-18
NO, I love user switching. I don't like switching with no password promt. ;)
Btw - I did disable account named guest with passwd -l, and verified that there is '*' in the second field. 
Restarted the system - but that option for password-less Guest session is still there...:o

---

### Post by John Bean on 2009-11-18
See my edit :-)

---

