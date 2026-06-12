---
title: "deleting wine menu listings"
date: 2011-07-26
forum: General Help
---

### Post by Vansch76 on 2011-07-26
Hi Everyone

I am trying to uninstall a windows program under wine called IMVU chat.
I am using wine 1.2.2 under ubuntu 11.04 in classic mode.

the unistaller locks up an will not complete. (let it run for 20 minutes).

Did a manual delete of the directories, cleaned the registry using regedit,
cleaned the files in .wine directory of anything that said imvu.

rebooted, and I still have a menu listing under wine, for IMVU.
clicking on a menu item says file not found.

My problem is I cant find where wine keeps it menu listing for installed programs.

I did find instructions for how to remove every menu at winehq, but not
how to just delete a single item.

Anyone know where this is stored at?

Thanks in advance for your help

Vanessa

---

### Post by CatKiller on 2011-07-26
Delete the appropriate files from ~/.local/share/applications and ~/.config/menus/applications-merged. ~/.local and ~/.config are hidden by default, so use Ctrl-H to show them.

---

### Post by Vansch76 on 2011-07-27
thanks 

that took care of it

Vanessa:popcorn:

---

