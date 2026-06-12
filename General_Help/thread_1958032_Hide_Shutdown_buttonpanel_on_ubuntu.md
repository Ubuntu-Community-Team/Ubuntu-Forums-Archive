---
title: "Hide Shutdown button/panel on ubuntu"
date: 2012-04-13
forum: General Help
---

### Post by kdismal on 2012-04-13
Hi All,

I'm a bit new to running ubuntu, but I'm trying to write a script to hide the shutdown panel/button on the top right of the screen. This is because others are using my computer and shutting it down and losing all my progress. I want a script where I can automate the process of hiding it. It doesn't matter to me if they run shutdown on the terminal or physically press the showdown button, just the button that has logout, restart, shutdown.

Any help possible would be greatly appreciated!
I've figured out how to restore it with: 
killall gnome-panel

---

### Post by jadtech on 2012-04-13
i dont know about hiding that menu  , how ever the account is set by default to hibernate and lock after a few mins Idol you cant get back without a password ..
i would think you could also set it to not shutdown without password..

---

### Post by kdismal on 2012-04-13
I think I'm looking more into the lines of using gconftool-2 --unset since I want to put it into a script. But I'm not sure what the command for the shutdown panel only is.

---

### Post by kdismal on 2012-04-13
I've figured it out!

for anyone interested in knowing, I did:
gconftool-2 -t list --list-type string -s /apps/panel/general/applet_id_list [trashapplet_screen0,workspace_switcher_screen0,window_list_screen0,show_desktop_button_screen0,indicator_applet_screen0,notification_area_screen0,clock_screen0]


basically, "/apps/panel/general/applet_id_list"
has a list of applications on the panel. All I did was remove the one panel I didn't want.

You can get the list of all panels by:
gconftool-2 -g /apps/panel/general/applet_id_list

---

