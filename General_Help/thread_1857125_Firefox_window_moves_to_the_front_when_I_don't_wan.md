---
title: "Firefox window moves to the front when I don't want it to"
date: 2011-10-09
forum: General Help
---

### Post by KingYaba on 2011-10-09
Let's say I'm working on something in Gimp and Pinta. Firefox, which is either minimized or behind the Gimp and Pinta windows, will suddenly move itself on top. This is incredibly annoying because I'm trying to concentrate. In the past hour it kept doing this to where I had to close Firefox and use Opera instead. Do you have any idea why this is happening? This is a recent phenomenon. I'm using Firefox 7 and Ubuntu 10.04 and it's not like I'm selecting *always on top*.

It's not a specific web page that causes this. Even on blank pages it will eventually move itself to the foremost window. Disabling addons doesn't help either.

---

### Post by mikejonesey on 2011-10-09
delete the js file in the profile folder of firefox, once in a blue moon it gets buggy... (all ways backup... maybee try ```
cd; mv .mozilla/firefox/profiles/squilyboo/profile.js .
``` squigboo being your random profile dir name n profile.js maybe someting else but its deffo the js file and i believe there is only one js file in the dir...)

just use the tab button alot for auto-complete...

---

### Post by lovinglinux on 2011-10-10
> **mikejonesey said:**
> delete the js file in the profile folder of firefox, once in a blue moon it gets buggy... (all ways backup... maybee try ```
cd; mv .mozilla/firefox/profiles/squilyboo/profile.js .
``` squigboo being your random profile dir name n profile.js maybe someting else but its deffo the js file and i believe there is only one js file in the dir...)

just use the tab button alot for auto-complete...

There is no such file in Firefox profile folder. I suppose you are referring to *prefs.js*. Indeed deleting the prefs file might solve the problem. But before deleting things I would start Firefox in safe mode, to see if there is an extension causing this problem. Also, test Firefox with a blank page, to see if the problem occurs independently of the content being viewed.

---

### Post by KingYaba on 2011-10-10
Having to redo my about:config tweaks and stuff doesn't bother me. I deleted the prefs.js so I hope this works. I couldn't tie this problem to an addon and it would pop up with blank pages.

edit: Still doing it.

---

