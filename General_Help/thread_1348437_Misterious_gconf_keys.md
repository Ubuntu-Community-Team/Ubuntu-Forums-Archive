---
title: "Misterious gconf keys"
date: 2009-12-07
forum: General Help
---

### Post by 6205 on 2009-12-07
I've uninstalled testing version of Avant Window Navigator and now i'm seaching for a way how to remove remaining gconf keys and clean my system, but so far without a success.

First i've cleaned all AWN reladed folders from my home dir. There were many hidden configuration folders and i'm sure they're all gone now, but gconf-editor is still without a change..

Then i've scanned my system with gconf-cleaner, but he have not found absolutelly nothing related to AWN. Same for Ubuntu Tweak when you clean configuration of removed stuff..

Any ideas where in file system should i search? I hate when i'm not i control :) I must kill those "registry" keys :)

---

### Post by 6205 on 2009-12-07
bump

---

### Post by pbrane on 2009-12-07
Use the --purge option
**sudo apt-get --purge remove *awn-whatever***
You should be able to just delete the keys in gconf too.

---

### Post by 6205 on 2009-12-07
> **pbrane said:**
> Use the --purge option
**sudo apt-get --purge remove *awn-whatever***
You should be able to just delete the keys in gconf too.

I cannot purge what is not installed. It's not working.
Also deleting gconf keys is not possible.

---

### Post by pbrane on 2009-12-07
gconftool-2 --recursive-unset /apps/avant-window-navigator
gconftool-2 --recursive-unset /apps/awn-

and so on...

if you delete all the keys under say *avant-window-navigator* the top level key will be deleted as well. You will need to close the config editor and reopen to see the changes.

---

### Post by 6205 on 2009-12-07
> **pbrane said:**
> gconftool-2 --recursive-unset /apps/avant-window-navigator
gconftool-2 --recursive-unset /apps/awn-

and so on...

if you delete all the keys under say *avant-window-navigator* the top level key will be deleted as well. You will need to close the config editor and reopen to see the changes.

Not working :( Also tried with sudo, but no response from terminal and also after full reboot are those keys still present..

---

### Post by pbrane on 2009-12-07
You may not have all of AWN uninstalled. Have a look at these.
[https://answers.launchpad.net/ubuntu/+source/gconf-editor/+question/38427]("https://answers.launchpad.net/ubuntu/+source/gconf-editor/+question/38427")

[https://answers.launchpad.net/ubuntu/+source/gconf-editor/+question/90632]("https://answers.launchpad.net/ubuntu/+source/gconf-editor/+question/90632")

I'm not sure why you can't unset those keys. I use gconftool-2 myself and have been able to unset and set keys with no issues.

---

### Post by 6205 on 2009-12-07
Those links did not provided any help to me, but thanks for your effort.. It looks like gconf is worst "registry" clone, without a possibility to delete anything from it :( Even if those keys/folders don't have any impact on system stability/performance, it's frustrating.. It could be also in the future a potential Ubuntu slowdown cause after some years using LTS version, who knows what kind of garbage have users in their gconf..

---

### Post by 6205 on 2009-12-07
bump

---

### Post by pbrane on 2009-12-07
I'm sure this is frustrating for you. I just used gconftool-2 to recursive unset /apps/dvd95 and it removed all of it including the top level. There must be something else that is causing this.

You say you installed the testing version of AWN. How? deb file, build from source? If you installed from deb file you would have removed using the same. If you installed from source you should have done a **make uninstall**. But still that may not remove the gconf entries.

It would be nice to have a context menu in gconf-editor that would allow you to delete an entire key and sub keys. At this point you still should be able to unset all the keys on the right hand side in gconf-editor and get rid of those keys. It looks like a lot of work though.

Found this:

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=933&page=1&isLive=true]("http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=933&page=1&isLive=true")

Maybe this will help.

---

### Post by 6205 on 2009-12-07
I've installed from AWN testing PPA for ubuntu karmic..

---

### Post by pbrane on 2009-12-07
you could always try re-installing and then remove with
**sudo apt-get --purge remove *awn-deb-file***

but I don't think that will remove the gconf entries.

---

### Post by 6205 on 2009-12-07
> **pbrane said:**
> you could always try re-installing and then remove with
**sudo apt-get --purge remove *awn-deb-file***

but I don't think that will remove the gconf entries.

You're right. I've already tried that :( I guess i must live with that..

---

### Post by phenest on 2010-01-30
I'm trying to do the same thing. And they will not unset. In fact, if you unset a name and value from the editor, they appear to delete. Close the editor and reopen it, et voila! They are all back.

---

### Post by phenest on 2010-01-30
I tried using --recursive-unset with a gnome panel to see what would happen:
```
gconftool-2 --recursive-unset /apps/panel/toplevels/bottom_panel_screen0
```
...and it works!

So what is keeping the AWN keys there? Is something replacing them? Weird!

---

### Post by mc4man on 2010-01-30
For apps you removed (or borked), you can look in ~/.gconf for a folder and delete it. All the keys should be gone on a restart

---

### Post by phenest on 2010-01-30
> **mc4man said:**
> For apps you removed (or borked), you can look in ~/.gconf for a folder and delete it. All the keys should be gone on a restart

Done that already, and no change.

---

### Post by phenest on 2010-01-30
In fact, after making sure awn and all applets and libraries are purged, then removing any files in the filesystem and /home folders, them damn entries remain in the gconf-editor!

---

### Post by phenest on 2010-01-30
To add to the mystery:
```
gconftool-2 --dump /apps > gconf.xml
```
If you look, there are no keys for awn anywhere. It seems that gconf-editor is having problems.

A bug maybe?

---

### Post by phenest on 2010-01-31
I've had an update to gconf, and it all is now ok.

---

### Post by mrsurb on 2010-04-20
I succeeded in removing them by manually editing /var/lib/gconf/defaults/%gconf-tree.xml and rebooting.

---

