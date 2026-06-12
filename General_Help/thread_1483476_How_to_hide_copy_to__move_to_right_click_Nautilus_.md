---
title: "How to hide copy to / move to right click Nautilus menus?"
date: 2010-05-14
forum: General Help
---

### Post by TwistedLincoln on 2010-05-14
I'm not liking the new "copy to" and "move to" right click menu options that Nautilus provides in 10.04.  They move "rename" (which I use much more often) to a different relative position on the menu.

Is there a way to hide these two new options?  Or do I need to recompile from source to remove them?  If the latter is true, can someone point me in the right direction?

---

### Post by un234567 on 2010-05-15
Me tooooo, the right click menu is so crowded. I need to save space by removing those 2 since i consider them useless. Anyone?

---

### Post by junapp on 2010-05-15
I agree. Both of these imo should be part of the 'send to' option.

---

### Post by gadolinio on 2010-05-15
It would be great, indeed. I guess the setting could be somewhere in gconf-editor, but couldn't find it. Nor in a web search. There is an application that lets you add entires to that menu. Install it with sudo apt-get install nautilus-actions. I post this in case someone can find out where the newly created entries go, in order to look for the existing ones there.

---

### Post by gadolinio on 2010-05-15
> **gadolinio said:**
> It would be great, indeed. I guess the setting could be somewhere in gconf-editor, but couldn't find it. Nor in a web search. There is an application that lets you add entires to that menu. Install it with sudo apt-get install nautilus-actions. I post this in case someone can find out where the newly created entries go, in order to look for the existing ones there.

Well, nautilus-actions has its own keys in gconf-editor, so it doesn't allow to locate the desired entries :S

---

### Post by castironpants on 2010-05-23
Definitely something that needs to get fixed

---

### Post by TwistedLincoln on 2010-06-04
I really hope this isn't something that one has to change by recompiling Nautilus from source, but if that's what it takes, I'd be willing to do it if someone would point me in the right direction.

---

### Post by TwistedLincoln on 2010-06-05
I've found a solution, and it doesn't require recompiling!

Edit /usr/share/nautilus/ui/nautilus-directory-view-ui.xml

Do a search for "CopyToMenu" and "MoveToMenu"  They should each show up in two locations within the file.

To completely remove the Copy To menu entry, just delete everything between <menu action ="CopyToMenu"> and </menu> in both locations.  The same is true for the Move To menu, substituting "MoveToMenu" for "CopyToMenu" above.

Personally, I like both menus, I just don't like their location.  Luckily, you can move them around by adjusting their entries position in the XML file.  I put mine right above the "Duplicate" entry, so that the two new menus show up at the top of the menu section.  Remember you have to adjust the position in both places in the file for the fix to work.

I think I'm going to file a bug report on launchpad about this.  The default behavior is really annoying.

---

### Post by yetiman64 on 2010-06-05
Thank you, TwistedLincoln, On seeing your post with the how to, I immediately chopped those 2 annoying little blighters out of my laptop Lucid install.
Will save me lots of usage headaches in the future, once again thank you and much =D>.

---

### Post by gadolinio on 2010-06-06
> **TwistedLincoln said:**
> I've found a solution, and it doesn't require recompiling!

Edit /usr/share/nautilus/ui/nautilus-directory-view-ui.xml

Do a search for "CopyToMenu" and "MoveToMenu"  They should each show up in two locations within the file.

To completely remove the Copy To menu entry, just delete everything between <menu action ="CopyToMenu"> and </menu> in both locations.  The same is true for the Move To menu, substituting "MoveToMenu" for "CopyToMenu" above.

Personally, I like both menus, I just don't like their location.  Luckily, you can move them around by adjusting their entries position in the XML file.  I put mine right above the "Duplicate" entry, so that the two new menus show up at the top of the menu section.  Remember you have to adjust the position in both places in the file for the fix to work.

I think I'm going to file a bug report on launchpad about this.  The default behavior is really annoying.

Great! Thanks, TwistedLincoln!

---

### Post by blawiz1 on 2011-10-16
also you can make new menues and actions with: nautilus-actions-config-tool

---

