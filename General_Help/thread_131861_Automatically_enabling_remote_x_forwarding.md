---
title: "Automatically enabling remote x forwarding"
date: 2006-02-17
forum: General Help
---

### Post by dcroxton on 2006-02-17
I log into Ubuntu remotely a lot, and I would like to be able to run GUI applications.  The problem is that I always have to march down to the desktop and type "xhost +" first.  The same thing applies when I try to run mythtv, which is run as the mythtv user, which doesn't have x access by default.

I looked for a way to enable remote x forwarding at startup, but I haven't been able to find anything that didn't look very complicated, and this seems like a simple issue.  Can someone enlighten me how to do this automatically at boot time?

Sincerely,
Derek

---

### Post by twigboy on 2006-02-17
I believe you have to edit this file  /etc/ssh/sshd_config and switch X11Forwarding to yes.  Mine was set to no by default.
Then in the shell ssh -X [email]blah@blah.com[/email]

---

### Post by dcroxton on 2006-02-17
Thanks for the suggestion.  Unfortunately, it turns out that this was already on.  Also, I don't think  don't think it would solve the problem with other users not being able to use the Xserver.

Sincerely,
Derek

---

### Post by dcstar on 2006-02-17
[QUOTE=dcroxton]I log into Ubuntu remotely a lot, and I would like to be able to run GUI applications.  The problem is that I always have to march down to the desktop and type "xhost +" first.  The same thing applies when I try to run mythtv, which is run as the mythtv user, which doesn't have x access by default.

I looked for a way to enable remote x forwarding at startup, but I haven't been able to find anything that didn't look very complicated, and this seems like a simple issue.  Can someone enlighten me how to do this automatically at boot time?

Sincerely,
Derek[/QUOTE]
What is in System-Administration-Login Screen Setup-Security?

---

### Post by twigboy on 2006-02-17
What do you use to remote into another machine? ie terminal, app

---

### Post by dcroxton on 2006-02-19
Ah, thank you, I see that "Deny TCP connections to XServer" is checked, which is probably causing xhost - to be set by default.  To answer the other question, I usually use ssh (via cygwin), but there is also that question about other users on the same box, e.g. mythtv.  I'll see if this fixes it...

Sincerely,
Derek

---

