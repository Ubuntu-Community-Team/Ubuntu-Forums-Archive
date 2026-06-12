---
title: "Can't Run Any Programs"
date: 2009-11-27
forum: General Help
---

### Post by Penguin Guy on 2009-11-27
I was trying to install Mac4Lin 1.0 manually, I rebooted and all I see is my background and my mouse. I can move my mouse around, bring up the shutdown menu with [COLOR="Green"]Ctrl + Alt + Delete[/COLOR] and switch consoles using [COLOR="Green"]Ctrl + Alt + 1-7[/COLOR] but nothing else works. Anyone got any idea what could have gone wrong?

It's not just a case that the panels have disappeared, none of my shortcuts work either (including [COLOR="Green"]Alt + F2[/COLOR]).

**Edit: I've given up and restored my system from a backup.**

---

### Post by staf0048 on 2009-11-27
Hmmm...

It sounds as though your Gnome panels have been deleted from the startup process somehow.  Hit Alt + F2 and see what happens when you type "gnome-panel" - if it comes back to life, you should be able to add the panels back to your startup process by going to System/preferences/sessions.

---

### Post by Penguin Guy on 2009-11-28
> **staf0048 said:**
> Hmmm...

It sounds as though your Gnome panels have been deleted from the startup process somehow.  Hit Alt + F2 and see what happens when you type "gnome-panel" - if it comes back to life, you should be able to add the panels back to your startup process by going to System/preferences/sessions.
Nothing happens, the usual 'Run Program' dialogue does not appear.

---

### Post by Penguin Guy on 2009-11-28
Bump.

---

### Post by oldos2er on 2009-11-28
When you say you installed Mac4lin manually, what exactly did you do?

---

### Post by Penguin Guy on 2009-11-28
> **oldos2er said:**
> When you say you installed Mac4lin manually, what exactly did you do?
Moved the themes into ~/.themes/ and edited the index files so that the theme was called 'Mac' rather than 'Mac4Lin Theme 1.0'. I've just given up, I'm restoring the entire system from a backup.

---

### Post by oldos2er on 2009-11-28
You could've booted into recovery mode and undone those changes. Just FYI.

---

### Post by Penguin Guy on 2009-11-29
> **oldos2er said:**
> You could've booted into recovery mode and undone those changes. Just FYI.
I did try undoing the changes using gconftool in the console, but it didn't work. Thanks for the info though.

---

