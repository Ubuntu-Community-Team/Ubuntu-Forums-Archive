---
title: "Nautilus on 11.10 displaying home folder as desktop"
date: 2011-10-15
forum: General Help
---

### Post by Hornet.ch on 2011-10-15
Hi

I upgraded to Ubuntu 11.10 and in Unity 2D there was no desktop available. I then downloaded gnome-tweak-tool and enabled the option "Have file manager handle the desktop".

Unfortunately, my home folder is now displayed as the desktop instead of ~/Desktop. I read something on the internet about ~/.config/user-dirs.dirs to specify XDG_DESKTOP_DIR. But the settings in this file are correct.

What could be the problem? Does nautilus just ignore the freedesktop.org specification?

Hornet

---

### Post by mc4man on 2011-10-15
I would tell to to install dconf-tools & then open dconf-editor where you can adjust the nautilus pref.'s
It may work for you but that section tends to open in an almost impossible to use fashion, just a little slit that is hard to expand - screen

So open a terminal, run this & if needed then do a log out/in

```
 gsettings set  org.gnome.nautilus.preferences desktop-is-home-dir false
```

Edit: this is everything that should be seen in the nautilus pref.'s section in dconf with my current valuus
> :~$ gsettings list-recursively org.gnome.nautilus.preferences
org.gnome.nautilus.preferences always-use-browser true
org.gnome.nautilus.preferences always-use-location-entry false
org.gnome.nautilus.preferences bulk-rename-tool @ay []
org.gnome.nautilus.preferences click-policy 'double'
org.gnome.nautilus.preferences confirm-trash true
org.gnome.nautilus.preferences date-format 'locale'
org.gnome.nautilus.preferences default-folder-viewer 'icon-view'
org.gnome.nautilus.preferences default-sort-in-reverse-order false
org.gnome.nautilus.preferences default-sort-order 'name'
org.gnome.nautilus.preferences desktop-is-home-dir false
org.gnome.nautilus.preferences enable-delete false
org.gnome.nautilus.preferences executable-text-activation 'ask'
org.gnome.nautilus.preferences install-mime-activation true
org.gnome.nautilus.preferences mouse-back-button 8
org.gnome.nautilus.preferences mouse-forward-button 9
org.gnome.nautilus.preferences mouse-use-extra-buttons true
org.gnome.nautilus.preferences show-advanced-permissions true
org.gnome.nautilus.preferences show-directory-item-counts 'local-only'
org.gnome.nautilus.preferences show-hidden-files true
org.gnome.nautilus.preferences show-icon-text 'local-only'
org.gnome.nautilus.preferences show-image-thumbnails 'local-only'
org.gnome.nautilus.preferences sort-directories-first true
org.gnome.nautilus.preferences tabs-open-position 'after-current-tab'
org.gnome.nautilus.preferences thumbnail-limit uint64 10485760

---

### Post by Hornet.ch on 2011-10-15
Thank you very much! That worked like a charm!

---

