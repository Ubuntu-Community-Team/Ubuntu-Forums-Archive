---
title: "Changed user directory and only have access to shell. Please help."
date: 2009-07-16
forum: General Help
---

### Post by data079 on 2009-07-16
I recently was trying to give my profile root privileges so it would quite asking me for the password. But for some stupid reason I changed the user directory to root as well. All I have access to now is the root shell. I need a command to change the directories back. I've looked all over but cannot seem to find it. Any help would be great Thanks!

---

### Post by michy99 on 2009-07-16
What is the output from this command?```
ls -l /home
```

---

### Post by sisco311 on 2009-07-16
> **data079 said:**
> I recently was trying to give my profile root privileges so it would quite asking me for the password. But for some stupid reason I changed the user directory to root as well. All I have access to now is the root shell. I need a command to change the directories back. I've looked all over but cannot seem to find it. Any help would be great Thanks!

```
usermod -d /home/username username
```

---

### Post by data079 on 2009-07-16
Thanks for all your help. Thanks to you I'm writing this post from my Kubuntu gui.
Thanks again!

---

