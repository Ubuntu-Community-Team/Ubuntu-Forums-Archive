---
title: "Accidentally Disabled GUI"
date: 2009-09-26
forum: General Help
---

### Post by Timothy Benton on 2009-09-26
I disabled the logon screen GUI (forget the exact name of the service). I thought I didn't need it because I have autologin enabled. But now I have no GUI. What command can bring it back? I'm stuck in the black screen with the text... I can log in but it still stays in text mode.

---

### Post by renkinjutsu on 2009-09-26
try ```
sudo /etc/init.d/gdm start
```

---

### Post by Timothy Benton on 2009-09-26
It worked! Thank you so much.

---

### Post by renkinjutsu on 2009-09-26
no problem, just remember to re-enable the service before you reboot!

---

