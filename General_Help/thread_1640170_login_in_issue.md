---
title: "login in issue"
date: 2010-12-07
forum: General Help
---

### Post by wh20250 on 2010-12-07
I'm very new to Ubuntu and would greatly appreciate help with an issue I'm having.  I'm using 64 bit Ubuntu 10.10 on an Alienware m15x and everything was wonderful until just recently. Now my login password is not accepted. This is only an issue if I log out (I skip login on start up). If I lock the screen the password works. It also works for all authentications. But if I log out I can not log back in without restarting the computer.  I have already tried changing my password and reseting it using recovery mode and dropping to the root shell. I'd prefer to not reinstall but am afraid that is the only thing left that I can think of. Please help me avoid this.

---

### Post by wh20250 on 2010-12-07
Update:

I created a "Guest" user that is not password protected I have the same issue when choosing this account at the log in screen.

---

### Post by wh20250 on 2010-12-08
It's fixed now.  The issue was with a line in one of the pam files.

include common-pamkeyring

commenting this line out fixed the issue.  I didn't figure this out on my own a colleague found it.

---

