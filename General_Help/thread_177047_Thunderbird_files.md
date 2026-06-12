---
title: "Thunderbird files"
date: 2006-05-15
forum: General Help
---

### Post by Steven_B on 2006-05-15
I am sharing one Thunderbird profile among several users.  All of the home/*/.thunderbird directories are symlinked to the same directory, so all of the users can see the same set of e-mail.
The problem is that Thunderbird edits some of the files, and changes their ownership to the current user.  When a different user opens Thunderbird, it can't read the settings.  How do I permanently set the owner of the files, or otherwise fix this problem?

---

### Post by aysiu on 2006-05-15
Keep the owner as is and then just chmod it so that all the users in the same group can read/write/execute: ```
chmod -R 775 /home/username/.thunderbird
```

---

### Post by Steven_B on 2006-05-15
I had to chown the owner to root, as well as use chmod.
"chmod 775" made Thunderbird think the profile was in use, so I did 777.  So far, it seems to be working fine.
Thanks!

---

