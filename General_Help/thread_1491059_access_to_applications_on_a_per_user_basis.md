---
title: "access to applications on a per user basis"
date: 2010-05-23
forum: General Help
---

### Post by HyperFlexed on 2010-05-23
Hi,

I'm wondering if it's possible to control what applications are available to certain users on a per user basis.

My motivation:

I have separate logins for audio production and general admin. Under Applications > Sound & Video I have tonnes of audio apps, but as I never use these under my general admin account, there's little reason to list all of them.

Any ideas? Also, how is the applications menu configured? I'm wondering because I'd like to create some custom sections.

---

### Post by John Bean on 2010-05-23
You can edit the menus for each user as much as you want; it won't prevent the apps from being available but can certainly hide them from the menus. Editing is normally done by right-clicking on the menu and choosing  "Edit Menu" or by selecting "Main Menu" from Preferences; you can reorganise, add or remove items to suit your own purposes, but just unchecking an existing item is the simplest way to make it disapprear from the menu.

---

### Post by HyperFlexed on 2010-05-23
Interesting. Now I'm curious though, how can you allow/prevent the use of certain applications? Say I made an account for a family member and I only wanted them to be able to access certain programs. Is there some kind of user management tool that will do this? Or is the functionality somehow built into the OS?

---

### Post by Zemblan on 2010-05-23
You can broadly configure users access to various tasks by having a look at the "User Privileges" tab in the "advanced" section of the "Users and Groups" tool. You can find that in "System -> Administration -> Users and Groups"
I'm not sure but if you want to restrict access to particular applications on a per user basis you can use some combination of group and user executable permissions on the binaries for those apps.For example only giving members of a particular group permission to execute them (have a look at: [http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html) for more information).

---

### Post by HyperFlexed on 2010-05-23
I could use binary permissions and such, but I'm assuming this wouldn't get rid of the link in their applications menu. I just find it odd how the ubuntu software center doesn't have a notion of installing for a single user. There should be some kind of application access control.

That is, if I disabled an application for an account, they should neither be able to access it, nor add it to their menus (or have it as an option to add).

I guess this could be tricky in such a flexible environment.

---

### Post by John Bean on 2010-05-23
> **HyperFlexed said:**
> That is, if I disabled an application for an account, they should neither be able to access it, nor add it to their menus (or have it as an option to add).

You can remove the ability of a user/group to edit the menus in exactly the same way you deny them access to other programs, in this case the program alacarte.

A combination of pre-defined menus and group permissions should allow you to limit access in the way you want to the groups you want.

---

### Post by HyperFlexed on 2010-05-23
> **John Bean said:**
> You can remove the ability of a user/group to edit the menus in exactly the same way you deny them access to other programs, in this case the program alacarte.

A combination of pre-defined menus and group permissions should allow you to limit access in the way you want to the groups you want.

If I were to disable alacarte for a user, would they still have the option "edit menus" available on right click of the applications button? I know if they lacked permissions and clicked it, they'd get an error. Now I'm wondering if I can hide the option altogether.

Also, do you know where alacarte stores per-user setup in the home folder? It doesn't seem to have a folder of its own.

---

### Post by John Bean on 2010-05-23
Alacarte is just an editor for the GNOME menu data, it doesn't store a copy of its own. There's a lot of documentation about the GNOME menu system if you look; Alacarte can handle most of it but more complex requirements can be dealt with by manual editing of the menu files. I have no idea if "Edit Menus" can be removed from the GNOME context menu.

---

