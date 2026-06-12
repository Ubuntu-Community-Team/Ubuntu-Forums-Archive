---
title: "access NTFS partions"
date: 2006-04-30
forum: General Help
---

### Post by IsKall on 2006-04-30
I'm am trying to view some partions on my laptop, they are an NTFS-partions for my winXP ( who recently crasched and only gets the blue screen everytime I boot the OS, that OS really _sucks_)

But when I click the icon on Open for this mount, this error comes:
You do not have the permissions necessary to view the contents of "hda5".

How do I get this "permission" ?

And I have these partions as icons on my Desktop, how can I remove them? (the remove "link" is not shown), if I do unmount, will it only remove the icon or will it do something else?

Someone who can help me with this little thing? :)

---

### Post by bugnot on 2006-04-30
Try this

[https://wiki.ubuntu.com/FilePermissions?#head-f07608330977614cf72483cd645caf3fc1eded9d](https://wiki.ubuntu.com/FilePermissions?#head-f07608330977614cf72483cd645caf3fc1eded9d)

---

### Post by chriscando on 2006-04-30
Sounds like you need to edit you /etc/fstab file. Edit the line to something like this:
```
/dev/hda6       /media/hda5              ntfs noauto,users,exec,ro,umask=0222 0 0

```

specifically add "users" part so that any user can mount this volume.

---

### Post by IsKall on 2006-04-30
Will do that. :)

Thank you chriscando and bugnot :)

---

