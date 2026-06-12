---
title: "Permission problems?"
date: 2009-07-30
forum: General Help
---

### Post by Flexico on 2009-07-30
OK, I had to re-format my hard drive, so I copied my Linux "home" folder to an external hard drive, re-installed Ubuntu, and put my "home" folder back. Then, when I booted up, I got a few warnings about files not being owned by me. Most of my filesystem was owned by "root", so many programs couldn't use their own files. So, I ran a command to set all ownership to "flexico" (my admin account, also only account), and now I'm getting errors about not being authorized to do things! Not even asking for the admin password, just "nope, get lost". Like when I tried to install wireless driver and graphics driver.

---

### Post by merlinus on 2009-07-30
Try this:

```
chmod 644 /home/username/.dmrc
chmod 755 /home/username
```

If you get error messages, try adding sudo in front of each command.

---

