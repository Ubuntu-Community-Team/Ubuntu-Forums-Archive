---
title: "cannot login after theme change"
date: 2012-03-29
forum: General Help
---

### Post by sssuizaaa on 2012-03-29
Hello everyone,



After changing the gtk-theme in the gnome tweak took I was  taken out of the session to the login screen and now I cannot log in. I  can only log in using the guest account.
  So in the grub menu I selected the recovery mode and in the resulting  menu I selected root-drop to root shell prompt. Once there I did a  couple of things I've found in several pages and in the forums.
  1.gsettings reset org.gnome.desktop.interface gtk-theme
  This is what I got:
  **(process:642):WARNING**: Command line 'dbus-launch  –autolunch=4438d024dd45ef7fb2d3f4ab0000000f –binary-syntax  --close-stderr' exited with non-zero exit status 1: Autolaunch error:  X11 initialization failed.\n
  and nothing changes
  2.gconftool-2 --type=string -s /desktop/gnome/interface/gtk_theme Radiance
  with this I was trying to change the gtk theme to the Radiance one.  No strange message this time but it did not work either. I still cannot  log in.
  Any ideas please??
  

I found solution number 1 here [http://ubuntuforums.org/showthread.php?t=1928190](http://ubuntuforums.org/showthread.php?t=1928190) and I asked for a solution at that thread as well. Sorry to ask again but if I cannot find a solution I would be forced to reinstall Ubuntu which is really not that bad but it would be sad that the only solution I find is to have to reinstall the whole Ubuntu just because I wanted to change the theme. There should be an easier way.


Anyway, I would thank anyone who could help.


sssuizaaa

---

### Post by sssuizaaa on 2012-04-05
OK, I finally found how to solve this. In the login screen I did Ctrl+Alt+F1 and then I created a new user.  Login with that new user and went to usr/share/themes and deleted the  themes I had just installed. Then I could login again with my original  user.
  Hope this helps to someone
  Sssuizaaa

---

