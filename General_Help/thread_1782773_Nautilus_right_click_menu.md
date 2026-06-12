---
title: "Nautilus right click menu?"
date: 2011-06-15
forum: General Help
---

### Post by MyUsernameIsJoker on 2011-06-15
[COLOR=Black][SIZE=4][FONT=Arial Black]_***Okay,so I successfully created a right click menu in Nautilus Actions Configuration,But when I right click on a file it doesn't show that menu! I did not really create it,I just imported XML document,I clicked save when I done that,I still can't see the menus(I restarted and stuff)***_[/FONT][/SIZE][/COLOR]

---

### Post by inameiname on 2011-06-15
Are you using the default Nautilus Actions in Ubuntu Natty? If so, forget it. It's a newer version of the thing and there are a lot of bugs that need to be worked out. I suggest downgrading to the previous version. I'll attach a copy for you. Then simply put a hold on the package to prevent it from updating to the latest version, and voila, using this terminal command: echo "package_name hold" | sudo dpkg --set-selections.

Anyway, doing the above, I fixed all issues I had just like that. So much easier.

---

