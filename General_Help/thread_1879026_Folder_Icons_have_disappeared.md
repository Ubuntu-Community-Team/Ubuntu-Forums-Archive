---
title: "Folder Icons have disappeared"
date: 2011-11-10
forum: General Help
---

### Post by linuxaspirer on 2011-11-10
my folder icons have disappeared, you know how these things show up on the folder, like downloads with file icon, ubuntu one file icon, Home folder file icons they have disappeared. Just icons are there but there are no user interface on them.
 
I think I dont know whether something got wrong on the unity settings.
please help....

---

### Post by hwttdz on 2011-11-10
I think what's gone wrong is the xdg dirs setup, I'd 

"gedit ~/.config/user-dirs.dirs"

and make sure everything is pointing at the right places...  i.e. if you want ~/Downloads to be your download directory, then do

XDG_DOWNLOAD_DIR="$HOME/Downloads"

after you're done editing the file run "xdg-user-dirs-update" then logout and log back in.

---

