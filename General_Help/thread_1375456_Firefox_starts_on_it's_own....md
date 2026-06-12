---
title: "Firefox starts on it's own...??"
date: 2010-01-07
forum: General Help
---

### Post by robertcoulson on 2010-01-07
Can anyone tell me why Firefox starts up when I log into Ubuntu 9.10...Wasn't doing it before...???
Bob

---

### Post by michy99 on 2010-01-07
Make sure that all applications are closed, including Firefox. Go to System->Preferences->Startup Applications. Click on Options tab. Click "Remember Currently Running Applications." Log out. Log in again.

If it doesn't work, then do the same thing, but put a checkmark by  "Automatically remember running applications when logging out." Make sure everything is closed and log out. After you log in again, go back and remove the check mark.

---

### Post by HiImTye on 2010-01-07
[LIST=1]
[*]close everything
[*]alt+f2 (or 'run' from the menu)
[*]type in 'gnome-session-save -gui'
[*]hit ok or run or w/e
[*]a popup will come letting you know your session was saved
[/LIST]
alternately you can go to startup applications and then sift through it to find an entry with firefox and delete it

---

### Post by robertcoulson on 2010-01-08
Thanks, guys...your information worked perfectly....Thanks again
Bob

---

