---
title: "Clean KDE defualts"
date: 2011-04-26
forum: General Help
---

### Post by dh04000 on 2011-04-26
I made a custom desktop last year. It was gnome with plasma effects enabled. I deleted my desktop bars in order to make this effect. I deleted the KDE desktop, but now I've reinstalled is and want to use a vanilla KDE desktop, but I can't get my panels back...... It kept the old config files......

How do I delete the KDE desktop configs, so when reinstall the KDE desktop it is vanilla?

I'd prefer if these help instruction don't remove qt/kde from my desktop, just my config files. I don't want to lose my qt/kde dependent apps and have to reinstall them again in order to fix this.

---

### Post by Simian Man on 2011-04-26
Delete the ".kde" folder from your home directory should do the trick.

---

### Post by dh04000 on 2011-04-26
That worked perfectly.  :)

But now I have a new issue. I can't get the networking to work. No wireless or wired ethernet connection will work.

Is there a way to use the gnome network manager in KDE? I know that it works.

---

### Post by dh04000 on 2011-04-27
Bump

---

### Post by Simian Man on 2011-04-27
I think the command to run the Gnome Network Manager is "nm-applet".  I'm not sure if trying to run two at once will give you problems, and I'm not usre the best way to disable KDE's network manager.

I'm surprised you have this issue though.

---

### Post by techunit on 2011-04-27
Simian Man Deleting the .kde folder is not recommended anymore it is very destructive in kde 4. Getting a vanilla desktop can be achieved by going to something like activities and creating a new default and deleting the old one.

Hope this helps. I don't know if I can fix your networking problem though.

---

### Post by dh04000 on 2011-04-27
> **Simian Man said:**
> I think the command to run the Gnome Network Manager is "nm-applet".  I'm not sure if trying to run two at once will give you problems, and I'm not usre the best way to disable KDE's network manager.

I'm surprised you have this issue though.

Its why I never install Kubuntu first. No networking. Hasn't been since Hardy Heron. KDE just doesn't like my networking card I guess. Dell e1705.

I used to be able to use the gnome networkmanger or wicd. But the nm-applet command is not working. Even after a reboot. I'd like to avoid installing wicd, so my ubuntu networking manager is not removed.

---

### Post by bergfly on 2011-04-30
gnome and kde network managers are mutually exclusive. Wicd is a good compromise. I had endless problems with earlier KDE 4 network managers. (remember when you couldn't assign a static IP in early KDE 4 -now there was a show stopper.)

It has been great the past couple releases though, you might want to go ahead and give it a try.

---

