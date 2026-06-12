---
title: "FileZilla (error 13: Permission denied) Trying to Backup"
date: 2011-06-11
forum: General Help
---

### Post by DrKnobblez on 2011-06-11
I'm trying to backup my website via FileZilla.

I set the default local directory to: /home/knobblez/Documents/knobblez

When I right-click any file or folder(/forum) & 'download',
it gives me this error:

Directory '/forum' couldn't be created (error 13: Permission denied)

My guess is my computer is denying it access. But I don't know how to fix it. 

Thanks in advance ;)

---

### Post by 3xp10r3r|X13 on 2011-06-11
your need to run:
```

cd /
sudo mkdir forum


```

You are logged in as a standard user, not as a super user, therefore you are not able to do any changes to "/". That's why it tells you "permission denied". To bypass this, you perform your actions as a super user "sudo=super user do" or you log in as root, by going for "su", to do a lot of tasks as the root user. To exit this "su mode" you just press ctrl+d.

This does also apply for anything you're moving to "/". As a standard user, you are only allowed to do changes to "/home/username"

This was designed for security reasons. That way malicious programs can't do any changes to your system, without your permission.

---

### Post by DrKnobblez on 2011-06-11
Figured it was something like that. Many thanks friend

---

