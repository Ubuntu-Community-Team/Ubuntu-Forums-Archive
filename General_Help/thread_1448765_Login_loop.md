---
title: "Login loop"
date: 2010-04-07
forum: General Help
---

### Post by J V on 2010-04-07
From what google tells me this is a common bug from 5 years ago that still hasn't been fixed...

When I set session to "GNOME/Openbox" and log in, shortly after the loading "Bar" pops up, it kicks me back to the login screen: As if something killed restarted X, only faster.

This means it takes about 20 minutes to get started up as I have to start gnome, run openbox and setup programs and reset the amount of desktops because it won't just startup openbox from the beginning.

I'd give you logs but what I'm looking at here is a huge list of warnings and errors about completely unrelated tasks that mostly didn't happen anywhere near login attempts...

I'm stuck

Edit: After more googling I now know what I'm looking for:
(Username replaced with ?, as if a forum search woulden't show what it is anyway lol)
```
Apr  7 08:38:03 Jubuntu gdm-session-worker[1687]: pam_unix(gdm:session): session opened for user ? by (uid=0)
Apr  7 08:38:03 Jubuntu gdm-session-worker[1687]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  7 08:38:04 Jubuntu gdm-session-worker[1687]: pam_unix(gdm:session): session closed for user ?
Apr  7 08:38:21 Jubuntu gdm-session-worker[2265]: pam_unix(gdm:session): session opened for user ? by (uid=0)
Apr  7 08:38:21 Jubuntu gdm-session-worker[2265]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr  7 08:38:21 Jubuntu gdm-session-worker[2265]: pam_unix(gdm:session): session closed for user ?
```

---

### Post by J V on 2010-04-08
bump... Taking 3 minutes every boot to set everything up again is a pita :(

---

