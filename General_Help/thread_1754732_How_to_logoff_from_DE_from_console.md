---
title: "How to logoff from DE from console?"
date: 2011-05-10
forum: General Help
---

### Post by chirag64 on 2011-05-10
Sometimes my Ubuntu keeps hanging when Unity crashes, or due to some other reason.
Logging out and logging in again seems to solve this problem, but sometimes I cannot even access the terminal from the Desktop.
Is there any command that I can use from the console so that my session at the desktop environment ends and I log out?
I already tried **gnome-session-save --logout** but it doesn't work :(

---

### Post by hwttdz on 2011-05-10
Not quite what you're looking for but you can restart gdm.  "sudo service gdm stop" "sudo service gdm start", I don't know if "sudo service gdm restart" would accomplish the same.

---

### Post by tredegar on 2011-05-10
**Ctrl-Alt-Backspace** traditionally logs you out and restarts X.

But this needs to be explicitly enabled in ubuntu, because it is disabled by default.

I am not using unity. For me this is under System, Preferences, Keyboard, Layouts, Options, Key Sequence to restart the X server. Check the box.

---

