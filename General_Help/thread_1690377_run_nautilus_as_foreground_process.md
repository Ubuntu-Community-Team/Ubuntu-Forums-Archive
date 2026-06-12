---
title: "run nautilus as foreground process?"
date: 2011-02-18
forum: General Help
---

### Post by vxd240 on 2011-02-18
Hello,
When I run nautilus from the command-line, it automatically runs in the background.  How can I run it in the foreground?

I'm trying to script something like this:
mount mydrive
nautilus mydrive/
umount mydrive

This would ensure that the drive is unmounted upon the exit of nautilus.  Unfortunately, nautilus runs in the background and moves immediately to the next umount command.

Any help would be appreciated.  Thanks.

---

### Post by aeiah on 2011-02-18
its because nautilus isnt just the filemanager, it sorts out your desktop icons and wallpaper too, for example.

i use openbox and thunar by default, and so nautilus isnt running all the time. if i launch it with ```
nautilus --no-desktop
``` then it'll run like any other foreground application - but it may just fork to the background when you try it because its already running

---

### Post by aeiah on 2011-02-18
what are you trying to accomplish anyway? is this supposed to be some easy to use thing that an inexperienced user can do without the risk of damaging the filesystem or something? you could use thunar instead of nautilus, or plan a different way around whatever your problem is

---

### Post by vxd240 on 2011-02-18
Thanks for the quick reply, aeiah.  I didn't realize nautilus managed other aspects of the desktop.  I installed thunar and it works like a charm.  Thanks again.

---

