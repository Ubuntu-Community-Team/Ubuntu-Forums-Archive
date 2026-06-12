---
title: "BackInTime fails after upgrade to Karmic"
date: 2009-11-04
forum: General Help
---

### Post by odinb on 2009-11-04
Hi!

I recently (today) upgraded to Karmic, and now BackInTime does not work...
([http://backintime.le-web.org/](http://backintime.le-web.org/))

When I try to launch it I get the following message:
"Could not launch 'Back In Time (root)' Failed to execute child process "su-to-root" (No such file or directory)"

[IMG]http://www.flickr.com/photos/44330902@N04/4073967545/[/IMG]

If I go to applications > Right-click > Edit Menus > System tools > Back In Time (root) > right click > Properties, the command shown is "su-to-root -X -c backintime-gnome".

Anyone else had this issue? How can I solve it?

Tried to replace "su-to-root" with "sudo", but to no avail.

//Odin

---

### Post by odinb on 2009-11-04
Nevermind, ran the command in a terminal, and it told me the solution...



odinb@odinb-server:~$ su-to-root -X -c backintime-gnome
The program 'su-to-root' is currently not installed.  You can install it by typing:
sudo apt-get install menu
su-to-root: command not found

---

