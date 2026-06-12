---
title: "Which Bash Command Disabled"
date: 2009-10-29
forum: General Help
---

### Post by ic3man on 2009-10-29
Hi, I ran security hardening tool Bastille and from then i cannot login with GDM and i get a message saying
```

WARNING: 'which' not available; unable to set safe TMPDIR

```

Any suggestions?
Thank you!

---

### Post by hwttdz on 2009-10-29
Try the non-graphical login and see if you can get any helpful error messages.  So failsafe gnome, or ctrl+alt+f6 and login.

---

### Post by ic3man on 2009-10-29
yep i tried this is how i manage to login but i still get this message as a warning.

---

### Post by ic3man on 2009-10-29
when i ran which as my user i get permission denied.
How can i restore its permissions? for computer admins team?

---

### Post by ic3man on 2009-10-30
how can i change the permissions of bash commands?

---

### Post by hwttdz on 2009-10-30
Try changing the permissions of your /tmp directory to 777?  Maybe it somehow got changed.

---

### Post by ic3man on 2009-10-30
they are already 777...
and chowned by root i use another user

---

### Post by ic3man on 2009-10-31
its about the bash how can i change permissions of commands?

---

