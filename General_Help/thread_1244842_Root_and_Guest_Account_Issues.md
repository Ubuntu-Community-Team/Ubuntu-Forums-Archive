---
title: "Root and Guest Account Issues"
date: 2009-08-19
forum: General Help
---

### Post by wynncreations on 2009-08-19
When I am logged in as the admin/root like I normally would be my screen's graphics are horribly wrong and I cannot do anything. If i switch to the guest login everything is fine, but I cannot get anything to run as admin.

Anyone with ideas on this one? Nothing changed after a reboot, and a reinstall of Ubuntu 8.10.

Thanks,
Robert

---

### Post by CatKiller on 2009-08-20
> **wynncreations said:**
> When I am logged in as the admin/root 

Don't login as root, and don't call your user "admin." The first is just a bad idea and the second gives instant breakage.

How are they "horribly wrong?" If it's just that the monitor's refresh rate has been set incorrectly, you could reset the monitor settings for that user by renaming the ~/.config/monitors.xml file to something else.

---

### Post by The Cog on 2009-08-20
@CatKiller:
Out of curiosity, why does user admin break things? I don't care to actually try it.

@wynncreations:
It may be due to some of your personal settings that mess up the display. I have on rare occasion abandoned all my settings to start afresh in order to lose a mucked up gnome setting - they scatter their settings all around multiple hidden directories which makes it very hard to find out which settings file needs dropping. If you think bad settings is your problem, I suggest these two remedies (in this order):

First, try renaming your .config folder - many settings are in there.
* Log out, leaving the GUI at the username prompt. 
* Press Ctrl-Alt-F1 to get a TTY console
* Log in as yourself
* Use the command **mv .config .config-old**
* Press Ctrl-Alt-F7 to return to the GUI
* Log in and see if the problem is fixed.
Logging in will recreate a .config folder but without all the old settings. 

Secondly, abandon your old user directory comnpletely, creating a new one:
* Log out, leaving the GUI at the username prompt. 
* Press Ctrl-Alt-F1 to get a TTY console
* Log in as yourself
* Get out of the old directory using the command: **cd /**
* Become root using the command: **sudo -i**
* Make a new home using these commands (substitute your username):
cd /home
mv username username-old
mkdir username
chown username:username username
* Now you should be able to return to the GUI with Ctrl-Alt-F7 and log in. All your data and settings have been lost. You can use nautilus to go and find your data in /home/username-old and drag into your new home.

---

### Post by snowpine on 2009-08-20
Hi Robert, if I understand your description correctly, the reason is that Ubuntu's root account is locked by default, therefore it has no end-user configuration. Logging in as root is not "pretty" like logging in as a regular user. If you somehow logged in as root, you can lock it down again following these instructions (which also explain how to use "sudo" for admin tasks while logged in as a user):

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Hope that clears it up...

---

### Post by CatKiller on 2009-08-20
> **The Cog said:**
> @CatKiller:
Out of curiosity, why does user admin break things? I don't care to actually try it.

(One of) The group(s) that controls whether a user is able to run a command with *sudo* is called *admin*. When you create a user, the system will automatically create a group with the same name (*username*:*username*). Since this group already exists in the case of creating a user called *admin*, breakage occurs. You can't be sure whether the group *admin* is the one that should be there, or the one that's been created with the creation of the user *admin*.

---

### Post by The Cog on 2009-08-21
Doh! I should have thought of that.

---

