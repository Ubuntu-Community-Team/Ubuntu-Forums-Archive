---
title: "how do i get metacity to give focus to new windows"
date: 2009-09-25
forum: General Help
---

### Post by chriskin on 2009-09-25
what i need is when a new windows is opened, to be given focus

---

### Post by Brandon Williams on 2009-09-25
I don't see anything directly related to this in under System->Preferences->Windows, but in gconf-editor, I found the key /apps/metacity/general/focus_new_windows. The description of the key (at least on Hardy) isn't terribly helpful.

> It has two possible values; "smart" applies the user's normal focus mode, and "strict" results in the windows started from a terminal not being given focus.

It looks like your best bet is to set /apps/metacity/general/focus_mode to "click" and /apps/metacity/general/focus_new_windows to "smart". I'm not sure that will give you what you're looking for, but it's the only thing that looks promising to me.

---

