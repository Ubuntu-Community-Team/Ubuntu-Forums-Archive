---
title: "How?? Mount point email notification"
date: 2012-01-22
forum: General Help
---

### Post by codeblue2k on 2012-01-22
I have a small nettop headless install of Ubuntu running thats solely used for mounting and backing up my NAS to Crashplan. I'm looking for a way to get email notifications from my nettop when the mount points change. That way I informed right away that Crashplan is not backing up my NAS. Is there anyway of doing this??

Thanks!

---

### Post by codeblue2k on 2012-01-23
Can anyone help out with this?? Thanks

---

### Post by gsgleason on 2012-01-23
a scheduled (cron) shell script to look at the current mounts and if there is a difference, mail you.

---

### Post by codeblue2k on 2012-01-23
Thats what I thought and needed a little help working on.

---

### Post by gsgleason on 2012-01-23
It really depends on what your mounts should look like vs what they look like when there is an issue.

Can you provide examples?

---

### Post by codeblue2k on 2012-01-23
When they are not mounted the mount points are just empty folders. I don't plan on putting anything in them ever.

---

### Post by dcstar on 2012-01-24
[http://unix.stackexchange.com/questions/10870/detecting-that-a-device-is-mounted-to-a-particular-folder](http://unix.stackexchange.com/questions/10870/detecting-that-a-device-is-mounted-to-a-particular-folder)

---

