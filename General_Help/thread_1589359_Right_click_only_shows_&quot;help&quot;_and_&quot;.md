---
title: "Right click only shows &quot;help&quot; and &quot;about&quot;"
date: 2010-10-06
forum: General Help
---

### Post by Rimbaum on 2010-10-06
I'm running Ubuntu 10.04, and I recently have wanted to start changing some of my taskbar items around. The problem is, when I go to right-click on the taskbar, all I can see are the "Help" and "About" menu options. No preferences, no options to get rid of a taskbar item, no options to add a taskbar item... And I can't seem to find any way to get around this, either!

Any help would really be appreciated. It's not a major issue right now, but since I'm rearranging my desktop appearance, I'd rather get this taken care of as soon as possible.

---

### Post by whiskeylover on 2010-10-06
Can you post a screenshot?

---

### Post by Rimbaum on 2010-10-06
> **whiskeylover said:**
> Can you post a screenshot?

I apparently cannot take a screenshot while the menu is open.

EDIT: I found a way to take one.

---

### Post by whiskeylover on 2010-10-06
See if this setting is enabled
gconf-editor / apps / panel / global / locked_down 

If yes, uncheck it.

---

### Post by Rimbaum on 2010-10-06
> **whiskeylover said:**
> See if this setting is enabled
gconf-editor / apps / panel / global / locked_down 

If yes, uncheck it.

Thank you, that fixed it!

---

