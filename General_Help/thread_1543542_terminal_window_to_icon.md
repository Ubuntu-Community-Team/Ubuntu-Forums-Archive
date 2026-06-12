---
title: "terminal window to icon?"
date: 2010-08-01
forum: General Help
---

### Post by Muttley99 on 2010-08-01
I have a desktop computer and a NAS, running Kubuntu & Ubuntu. I use WOL to wake the NAS and then mount the drives (NFS) on my desktop.
I've placed an icon on my KDE desktop which wakes the NAS and mounts the drives, this works great, but I've set it to run in terminal so I can enter the password for mounting the drives. This leaves me with an open window which I don't want to close because the NAS is set to shutdown 15 minutes after ssh logout. 
My question is how can I minimise the open terminal window to an icon on my taskbar?

---

### Post by BenAshton24 on 2010-08-01
You could use AllTray ([http://alltray.trausch.us/](http://alltray.trausch.us/))

---

### Post by Muttley99 on 2010-08-01
Ben,
I already have alltray working to minimise my firestarter window. I assumed it would not work for the terminal.
I can get this to work with the terminal by manually selecting the window after entering alltray. I can't get alltray to run on startup for that specific terminal window. Any ideas?
I suppose I could add a cron job @startup but this seems a little bit extreme and I'm not sure it will work that well.

---

