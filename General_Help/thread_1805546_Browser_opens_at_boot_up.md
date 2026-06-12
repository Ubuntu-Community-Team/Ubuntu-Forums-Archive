---
title: "Browser opens at boot up"
date: 2011-07-16
forum: General Help
---

### Post by hardyfan on 2011-07-16
Hi,

I've just switched to Xubuntu (hate unity) however 20 percent of boot ups firefox opens automatically (small anoyance).  Can anyone tell me how to eliminate this problem ?


Thanks
Noel

---

### Post by Toz on 2011-07-16
XFCE allows you to save sessions when you logout (or directly from Settings Manager->Session & Startup->Session tab). If the checkbox to "Save session for future logins" is checked, it will restart those applications that are currently running. If you choose to keep the checkbox checked, make sure only the apps you want automatically restarted are running. The session configurations files are stored in ~/.cache/sessions.

Reference link: [http://wiki.xfce.org/faq#session_manager]("http://wiki.xfce.org/faq#session_manager")

---

### Post by hardyfan on 2011-07-17
Thank you, I have tested extensively and problem appears to be fixed.

Noel

---

