---
title: "No LightDM Greeter Wallpaper When User List is Hidden"
date: 2012-09-01
forum: General Help
---

### Post by floborg on 2012-09-01
If I disable the user list from the login screen, no wallpaper is shown - not even the default for 12.04.  Only when the user list is enabled is a wallpaper shown (mine).  I don't want the user list shown.

I hid the user list from lightdm in Ubuntu 11.10, and I was able to see a custom wallpaper in the greeter after editing the conf file.  Now, in 12.04, there's no wallpaper shown on the login screen.  The only way I've been able to see a wallpaper of any kind was to re-enable the user list on the login screen.  I've tried:

* Re-adding my wallpaper using the Appearances dialog
* Disabling dynamic wallpaper using gsettings/dconf-editor for the lightdm user
* Copying my wallpaper to /usr/share/backgrounds and putting that file path in the conf files and also in the gsettings key for lightdm; and, yes, the permissions were fine
* Changing the wallpaper using Ubuntu Tweak

Nothing worked.

---

