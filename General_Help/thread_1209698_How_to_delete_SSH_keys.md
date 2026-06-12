---
title: "How to delete SSH keys?"
date: 2009-07-10
forum: General Help
---

### Post by antdgar on 2009-07-10
I am currently renting an Ubuntu server and I want to delete the old SSH keys.
I want to delete them because the provider (OVH) is known to search around people's servers. They do this by using the default SSH keys which they put there...

How can I delete them?

---

### Post by pennacook on 2009-07-10
If it is just for a user, you can remove the user's .ssh directory. If for the server, remove the /etc/ssh/ssh_host* files. When SSH starts again, it will generate new keys. Curious as to why they wouldn't just reimage the system...

---

### Post by antdgar on 2009-07-10
> **pennacook said:**
> If it is just for a user, you can remove the user's .ssh directory. If for the server, remove the /etc/ssh/ssh_host* files. When SSH starts again, it will generate new keys. Curious as to why they wouldn't just reimage the system...
Thanks,

But I just tried dragging it to the recycle bin and it says 'ssh_host file cannot be deleted'??

[IMG]http://i187.photobucket.com/albums/x268/antdgar/Picture4-6.png[/IMG]
also should i delete the 'pub' files too?

---

### Post by CatKiller on 2009-07-11
> **antdgar said:**
> I just tried dragging it to the recycle bin

You might want to read [this page]("https://wiki.ubuntu.com/RootSudo").

The gist is that you need to temporarily become root to fiddle with anything outside your Home folder. In this case, you can use ```
gksudo nautilus
``` to open a file browser as root.

---

