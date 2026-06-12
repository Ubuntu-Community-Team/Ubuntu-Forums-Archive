---
title: "open a specific tomboy note with a command to create launcher"
date: 2010-07-15
forum: General Help
---

### Post by finny388 on 2010-07-15
I tried
```
tomboy --title-note "To Do"
```

but it returns
> [INFO 14:55:56.264] Initializing Mono.Addins


and opens in notification area.

but the note does not open.

anyone know how to code this?

thanks

---

### Post by sharm on 2010-07-16
> **finny388 said:**
> I tried
```
tomboy --title-note "To Do"
```

but it returns


and opens in notification area.

but the note does not open.

anyone know how to code this?

thanks

The command line option you want is --open-note, not --title-note.

---

### Post by finny388 on 2010-07-16
Thanks sharm.

That worked.

---

### Post by clockworkpc on 2010-07-22
I have a note that I'd like to update on the fly as I get new ideas.  For this it would be nice to have a keyboard shortcut that would open the note.

However...

clockworkpc@clockworkpc-laptop:~$ tomboy --open-note "To Do"
Tomboy is already running.  Exiting...

Is there a way of setting up a hot key for a specific note?

---

### Post by finny388 on 2010-07-22
creating a keyboard shortcut is pretty much a separate topic but here it is:

[LIST]
[*]Ubuntu Menu/System/Preferences/Keyboard Shortcuts

[*]Scroll to the bottom to get to Custom Shortcuts.

[*]There, click Add, copy your tomboy command into command, and give it a name. Click apply.

[*]Now click the word disabled next to your new command and press your keyboard short cut.
[/LIST]
That's it

---

