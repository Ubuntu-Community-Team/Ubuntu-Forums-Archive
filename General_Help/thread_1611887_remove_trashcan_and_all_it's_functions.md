---
title: "remove trashcan and all it's functions?"
date: 2010-11-02
forum: General Help
---

### Post by rkp71 on 2010-11-02
Can someone tell me how to remove the trash can and remove the send to trash when I right click something?

When I delete something I want it deleted.  When I right click an icon I want the delete option, not send to trash. 

I know I can at least select an icon hold shift and hit the delete key, and get asked once again if I permanently want to delete this file. At least in windows I could hold shift and right click the icon to select delete, now in ubuntu I hold shift and right click icon and I still only get send to trash and it ofcourse does just that, send to trash. 

I don't want to be asked, I don't want to have to delete my files twice.  Can I totally remove this bad windows idea called trash can, which unfortunately works even worse in ubuntu?

---

### Post by bowens44 on 2010-11-02
> **rkp71 said:**
> 
I don't want to be asked, I don't want to have to delete my files twice.  Can I totally remove this bad windows idea called trash can, which unfortunately works even worse in ubuntu?

I don't think it's a bad idea at all. but if you like , you can add a delete option to the context menu by checking that option in nautilus preferences.

Preferences and then, from the Behavior tab, check the box for Include a Delete command that bypasses Trash. After you have done that, click Close on the Preferences window and now, when you right-click a file, you will see a Delete entry.

---

### Post by blueridgedog on 2010-11-02
The second post here outlines how to disable the use of trash:

[https://bugs.launchpad.net/nautilus/+bug/118988](https://bugs.launchpad.net/nautilus/+bug/118988)

You can edit gconf with the gconf-editor tool.

---

### Post by rkp71 on 2010-11-02
Thank you for the replies. LOL, I should not expect this to ever get fixed I guess since it was reported in 2007 and you still can't disable the "windows" trash can.  If I could go back in time I would kill the person who invented the windows key, I guess while there I'll get the trashcan person as well.  :P

---

### Post by blueridgedog on 2010-11-02
The gconf edit should get you what you want.  The developers have not created a method inside nautilus to do it, but the method is there and only takes a few clicks.

---

