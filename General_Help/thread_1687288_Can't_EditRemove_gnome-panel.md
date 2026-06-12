---
title: "Can't Edit/Remove gnome-panel"
date: 2011-02-13
forum: General Help
---

### Post by shoot2kill on 2011-02-13
Hi, I went to rearrange the icons on my top gnome-panel today, as some of the notification icons are displayed to the right of the power menu, and whenever I right click on any gnome panel, I get two options only 'Help' and 'About Panels'

the menu options for edit, move, remove etc. are gone.

I don’t really know where to start with this, as I don’t think I have tried to edit the panel since a clean install, so don’t know when it was last OK.

Any help would be greatly appreciated.

Thanks

---

### Post by sikander3786 on 2011-02-13
Might be there is some applet running taking up the whole of your panel? Can you please post a screenshot.

---

### Post by gerowen on 2011-02-13
You can also try restarting gnome panel with:
```
sudo killall gnome-panel
```
Sometimes when a widget fails to load on login this helps me give it a chance to restart.

---

### Post by shoot2kill on 2011-02-13
Screenshots:

Only one screenshot could be taken as screenshots cant normally be taken whilst context menu is open, but every other panel shows the same context menu, but only showing an 'About' option.
[[IMG]http://img6.imagebanana.com/img/j9b725pu/thumb/Tooltip_003.png[/IMG]](http://www.imagebanana.com/view/j9b725pu/Tooltip_003.png)

The 'About' for all working panels:
[[IMG]http://img6.imagebanana.com/img/6gqp49pm/thumb/Workspace1_008.png[/IMG]](http://www.imagebanana.com/view/6gqp49pm/Workspace1_008.png)

restarting the process or the system does nothing to change the problem.

---

### Post by gerowen on 2011-02-13
If you create a new user and log in with that user does the problem exist?  If not, it could be just a funky setting with your gnome settings.  Just open up a terminal and run:
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```
Then restart your computer and your Gnome should be reset to its system defaults.

---

### Post by shoot2kill on 2011-02-13
The new user showed that it was some bad settings, and removing the directories worked.

Thanks alot! :)

---

### Post by seanos on 2011-06-24
I encountered this problem (or something very similar) recently and found the answer was a setting in gconf-editor that had been switched on somehow - /apps/panel/global/locked_down.  Worth checking before deleting all your settings!

---

