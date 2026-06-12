---
title: "How to get back update notifications in 9.10?"
date: 2009-11-11
forum: General Help
---

### Post by david.karr on 2009-11-11
In 8.10, when an update became available, I would get an icon alert in the top panel.  When the update was done, if something I updated required a restart to use, then it would indicate that.

In 9.10, I appear to have at least lost the first capability, and perhaps the second.

I believe this is a well-known problem now, but I'm having trouble getting through all the noise to a solution to this problem.  Is there a way to get back how this worked in 8.10?

---

### Post by bashphoenux on 2009-11-11
press alt+f2 and type
update-manager 
and the update manager icon will appear only when there are updates pending to be installed!! or if they are released only!! if your system is upto date then it wont show up
and regarding distro upgradation
in the above command add -d
update-manager -d 

hope it helped :)

---

### Post by david.karr on 2009-11-11
I don't understand.  Alt-f2 brings up a dialog to enter an application to run.  You're suggesting I run "update-manager".  You're saying that somehow the "icon will appear only when there are updates pending"?  That makes no sense.

---

### Post by Aearenda on 2009-11-11
Since 9.04 the Update Notifier has popped up a window when it has updates to show. Prior to 9.10 it stuck an icon in the notification area. You can revert to the old behaviour by:-
1. Start gconf-editor by pressing ALT+F2 and typing gconf-editor<enter>
2. Find and select 'update-notifier' under 'apps'
3. In the right pane, uncheck the key 'auto_launch'

That's it. There are many long discussions over the rights and wrongs of this, I'm just relaying what I've seen in different places.

Edit: Running Update Manager itself isn't the answer to the OP's problem.

---

### Post by jeb800e on 2009-11-11
System > Administration > Update Manager

---

