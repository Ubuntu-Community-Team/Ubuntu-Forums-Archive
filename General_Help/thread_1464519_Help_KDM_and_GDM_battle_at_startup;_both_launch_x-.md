---
title: "Help: KDM and GDM battle at startup; both launch x-servers"
date: 2010-04-28
forum: General Help
---

### Post by Adam's AI on 2010-04-28
Hi,
    I have both ubuntu and kde-desktop installed, and after trying KDM, switched back to GDM which worked fine for a while (although KDE changed my other gnome settings like usplash and cursors which took a while to change back). A day later, though, when I start up my system, the screen flickers a few times then shows me a message that an x-server is already running, so hit no to try loading it on '0' again or yes to try another number. If I hit no, it will briefly show me the KDE login screen refresh a few times and go back to the menu. If I hit yes, it refreshes about 7 times and finally shows the gnome login screen. This process takes a long time and I'm not sure is great for my screen. Any suggestions on how to remove the duplication?

Any help would be appreciated!

-Adam

---

### Post by Adam's AI on 2010-04-28
Probably should have posted this to the desktop environments category. If an admin could move it, that would be great.

---

### Post by klemes on 2010-04-28
I think this might help:

```
sudo update-alternatives --config x-session-manager
```

If not this exactly try searching for the correct symlink in the /etc/alternatives directory and substitute in the above command accordingly after config.

---

### Post by Adam's AI on 2010-04-30
Thanks for the tip. I gave it a try, and the default was set to a gnome session. I had previously tried setting the gdm using "sudo dpkg-reconfigure gdm"

The problem seems to be happening some times but not others. Since lucid just came out, I'll try updating and see how my system behaves.

I wonder if there is a general problem with KDE. After installing it, it reset my default cursors and usplash as well, and they would not easily change back as they should using the update-alternatives. The only way I got my cursors back was by [accidently deleting x-cursor-theme]("http://ubuntuforums.org/showthread.php?p=9183679"). Do you think it's worth uninstalling KDE?

---

