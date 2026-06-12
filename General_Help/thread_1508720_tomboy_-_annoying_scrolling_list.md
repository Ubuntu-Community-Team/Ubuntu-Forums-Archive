---
title: "tomboy - annoying scrolling list"
date: 2010-06-13
forum: General Help
---

### Post by dimeotane on 2010-06-13
Can any Tomboy users confirm for me if clicking on the Tomboy icon causes a long list of notes to scroll downwards?  Is this a new 'feature' or a bug I have?  Its annoying as heck.  I've only got 9 of them set to a green sticky, but the list is so full of notes it spills off the screen.  It used to be that only what was set to sticky would show on the list and it wouldn't scroll all the way off the edge of the screen.  Anyone have any ideas how to fix this?

---

### Post by sharm on 2010-06-25
If you're using Maverick, I believe they are patching in appindicator support so that could be causing this.  If that's the case, you should report a bug in launchpad.

If you're using a stable Tomboy release, you should not be seeing this behavior.  Tomboy shows in the menu all pinned notes, all opened notes, and (by default) the 10 most recently edited notes.

It's possible, though unlikely, that you have edited the gconf value that says how many recent notes should be shown.  You might want to check /apps/tomboy/menu_note_count in gconf-editor.

---

