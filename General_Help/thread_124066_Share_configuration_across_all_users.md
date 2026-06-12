---
title: "Share configuration across all users"
date: 2006-01-31
forum: General Help
---

### Post by whisperer on 2006-01-31
How is it possible to make all users share the same initial settings in *all* programs (desktop, panels, keyboard shortcuts, Firefox plugins, etc.) ? Of course a user can override any of these settings individually, but I want to change several default settings globally.

---

### Post by dcstar on 2006-01-31
[QUOTE=whisperer]How is it possible to make all users share the same initial settings in *all* programs (desktop, panels, keyboard shortcuts, Firefox plugins, etc.) ? Of course a user can override any of these settings individually, but I want to change several default settings globally.[/QUOTE]
Common Firefox plugins should be installed in the Firefox binary directory tree, not the user .mozilla tree.

As far as the others are concerned, there should be default configuration files that you can modify, but you will probably have to find them yourself.

---

### Post by BigMurph on 2006-01-31
You can add files from your home directory to /etc/skel and they will be in the home directory of any new users created. As for users already created you can copy the relevant ~/.whatever directory into their home (as root) and then do a chown *user:group* /home/*user*/.whatever to give them the proper permissions.

For instance to copy your panel to another user's account (let's say Jim's) you might use

sudo cp -r ~/.gnome2/panel2.d/* /home/jim/.gnome2/panel2.d/
sudo chown -r jim:jim /home/jim/.gnome2/panel.2d

The commands might not be spot on perfect but they should give you an idea how to start. Check the man pages for correct syntax, etc. (eg. type "man chown" in terminal)

Hope this helps,

Murph

---

### Post by whisperer on 2006-01-31
The cp/chown solution was more or less what I had in mind if there wasn't an automated way (though I didn't know about /etc/skel; thanks! :)). Still, the main problem remains: which files to copy ? You can't just copy every hidden file of the root's home; some don't have to or should not be copied (e.g. .Trash/*, Firefox's bookmarks, mailboxes, etc.) :-k

---

