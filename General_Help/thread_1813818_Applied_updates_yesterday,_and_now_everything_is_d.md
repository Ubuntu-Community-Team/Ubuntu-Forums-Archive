---
title: "Applied updates yesterday, and now everything is different?!"
date: 2011-07-28
forum: General Help
---

### Post by ksaul on 2011-07-28
I applied the updates that were in my Update Manager yesterday, and i was informed to restart - did so, and now everything looks different... its all boxy, and my color scheme has changed (even though under Appearance Preferences, I am still using the same theme...??)

I tried switching themes, and then switching back to my original theme (Ambiance), but still I have this 'windows' (more like windows 98...) like appearance, and was wondering what update did this, and how to fix it back to look nice & clean again.

Even my terminal server appearances changed, it was black background with white text, and now its white background with black text (I fixed it, but I had to manually change the colors)

any help would be great - would really like my smooth, clean and pretty ubuntu back :(

---

### Post by CatKiller on 2011-07-28
Sounds like gnome-settings-daemon (which applies your themes and so on) isn't working. Open a Terminal (so you can see any error output) and run gnome-settings-daemon.

---

### Post by ksaul on 2011-07-28
> **CatKiller said:**
> Sounds like gnome-settings-daemon (which applies your themes and so on) isn't working. Open a Terminal (so you can see any error output) and run gnome-settings-daemon.


seems like your right:

```

kevin@kevin-Studio-XPS-8100:~$ gnome-settings-daemon

** (gnome-settings-daemon:14638): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:14638): WARNING **: Could not acquire name
```

I am using ubuntu 11.04 64bit - what do i need to do to fix this?

---

### Post by turtle153 on 2011-07-28
Seems like your gnome-settings-daemon is working fine. Have you tried restarting though? It's always fixed it when I have this problem.

---

### Post by ksaul on 2011-07-28
> **turtle153 said:**
> Seems like your gnome-settings-daemon is working fine. Have you tried restarting though? It's always fixed it when I have this problem.

yes i restarted after i applied the updates (which caused the issue) -- and then changed my theme to another one, and then back to my original theme - and then restarted again - still looks funky =(

---

### Post by 4Orbs on 2011-07-28
If you are using the proprietary driver for your video card, you can try deactivating it (Additional Drivers in the System Menu) then reboot and reactivate it.

---

### Post by ksaul on 2011-07-28
actually I think it has to do with System Settings? I managed to change most things back to what they were before although some things still look strange

---

