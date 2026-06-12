---
title: "Can't Change Display Size"
date: 2009-07-03
forum: General Help
---

### Post by gutierrezfam on 2009-07-03
Hi all.  I've just installed Kubuntu 9.04 on my Dell Inspiron 518 desktop.  The default display resolution is a blocky 640x480. I run 1600x900 on Vista.

When in the Display-System Settings window (Size & Orientation tab), if I change the Display Size from 640x480 to anything else, then click Apply, the size automatically goes back to 640x480 without any visible change.

Can anyone help out?  Thanks in advance.

---

### Post by TeoBigusGeekus on 2009-07-04
Have you installed the restricted drivers?

---

### Post by gutierrezfam on 2009-07-04
I assumed that the restricted drivers were installed automatically, and that I'd just enable them.  Now that you mention this, I think I did notice that the list was empty where I pulled up the restricted drivers window.

So how do I install them?  Thanks.

---

### Post by Tews on 2009-07-04
> **gutierrezfam said:**
> I assumed that the restricted drivers were installed automatically, and that I'd just enable them.  Now that you mention this, I think I did notice that the list was empty where I pulled up the restricted drivers window.

So how do I install them?  Thanks.

```

sudo apt-get install ubuntu-restricted-extras

```

You also might need to edit your xorg.conf file a bit, but lets see what happens ...

---

### Post by gutierrezfam on 2009-07-04
Thanks, Tews.

Good and bad news...  ran the apt-get command you suggested.  Rebooted.  When the login window came up, I immediately noticed the increase in resolution.  Looked very good!  After entering my password, things went down hill.  The window that shows the various icons (hard drive, tools, etc.) blinked frequently.  It also took much longer to go through this task.  Then I was finally "in".  High resolution desktop and taskbar on the bottom.  HOWEVER...  The background toggled between the default gray scheme (usually displayed when the windows desktop is still booting up) and the default blue scheme (indicating everything's up and running).  Likewise, the task bar at bottom toggled from being displayed to not.  The problem is it never stabilized (toggled endlessly), and none of my mouse clicks didn't do anything at all.  I had to bring up a full-screen terminal (via alt-F?) and did a "sudo shutdown -r now".  I'm typing on Vista again... which is what I'm trying to steer away from.

Any ideas?

---

