---
title: "Comiz quit working on startup"
date: 2009-07-29
forum: General Help
---

### Post by 68pontiac on 2009-07-29
So, to keep it short I broke my X recently on my Jaunty machine. I ran the dpkg-reconfigure routine and restored my config and I also removed and reinstalled the proprietary ATI video drivers (from ATIs site, not the Ubuntu ones that never work for me). Now, I can boot into the system again and everything is fine except I have to either open a terminal to run compiz or use fusion-icon and tell it to "Reload Window Manager" each time.

What can I do to make certain that Compiz loads on startup each time? I already have a startup command for fusion icon (fusion-icon --no-start) but I still have to tell it to reload before I get compositing. Any help would be appreciated. THANKS!

---

### Post by CatKiller on 2009-07-29
I think setting the /desktop/gnome/applications/window_manager/default key in gconf-editor to /usr/bin/compiz will do this.

---

### Post by 68pontiac on 2009-07-29
Thank you for the reply. Compiz is already set up as the default window manager in Configuration Editor.

As it stands now it reads:
```
current compiz
default /usr/bin/compiz
```

Any other suggestions? I feel that this may be in some way related to me recently installing the fusion-icon package but I have removed it completely and the problem still persists. I'm thinking I might completely remove Compiz and reinstall it if I can't think of any better idea.

---

### Post by CatKiller on 2009-07-29
Rather than running your fusion-icon at startup, you could run ```
compiz --replace
``` at startup instead. It seems like an overkill solution, though.

Otherwise, you could change the current key to /usr/bin/compiz, too.

---

### Post by 68pontiac on 2009-07-29
I'll give that suggestion a go and report the results. I just don't get why I'd have to do this now but never had to do it before I broke X. Is there any configuration stuff regarding Compiz in X11.conf ?

---

### Post by CatKiller on 2009-07-29
Actually, the newer way of doing things is with the fake window manager gnome-wm (which should be selected by the /desktop/gnome/session/required_components/windowmanager GConf key). If that's set to metacity, for example, then metacity is what will be loaded instead.

This is what gnome-wm's man page says:

> **DESCRIPTION**
       The _gnome-wm_ script invokes the user selected window manager.   If  the
       user  has  not chosen a window manager it will launch a GNOME compliant
       window manager.

       The user can overwrite the selection of a window manager by setting the
       **WINDOW_MANAGER** environment variable.  If a **--default-wm** option is given
       the script uses that window manager in case **WINDOW_MANAGER** is not  set.

gnome-wm is a script that's stored in /usr/bin. You could edit it with a text editor run as root if it turns out that the DEFWM= line has anything in it..

---

### Post by CatKiller on 2009-07-29
> **68pontiac said:**
> I just don't get why I'd have to do this now but never had to do it before I broke X.

Because you broke X.

Most scripts have fallback values. I'd imagine that when you broke X the fallback of metacity was selected and stored somewhere. When you fixed it, you probably did something different to the scripts that got run when the system was first installed, and so that value wasn't updated. Your task is to pretend to be the scripts, so that you can change the appropriate value :)

---

