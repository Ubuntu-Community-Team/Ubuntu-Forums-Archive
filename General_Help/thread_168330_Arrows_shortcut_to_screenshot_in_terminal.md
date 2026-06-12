---
title: "Arrows shortcut to screenshot in terminal?"
date: 2006-04-30
forum: General Help
---

### Post by gumbald on 2006-04-30
Whenever I'm in the terminal window and press one of the directional arrows, it brings up the screenshot dialog, very frustrating! Any ideas how to stop this?

Cheers,
Jamie

Edit: It's WHENEVER I press an arrow key!

---

### Post by henriquemaia on 2006-04-30
[QUOTE=gumbald]Whenever I'm in the terminal window and press one of the directional arrows, it brings up the screenshot dialog, very frustrating! Any ideas how to stop this?

Cheers,
Jamie[/QUOTE]

You're using the default gnome terminal? What arrows, the simple ones or the numeric keypad ones?

Check under: System --> Preferences --> Keyboard Shortcuts

To see what shortcut you have assigned to take a screenshot.

---

### Post by gumbald on 2006-04-30
Yep, checked that, it's just the default "Print" button. I think it started after I double pressed tab to bring up the list of files when navigating to a particular one.

---

### Post by henriquemaia on 2006-04-30
[QUOTE=gumbald]Yep, checked that, it's just the default "Print" button. I think it started after I double pressed tab to bring up the list of files when navigating to a particular one.[/QUOTE]

But it happens all the time you open a new terminal window? Have you tried to logoff-logon (restart if you prefer) and test it again?

---

### Post by gumbald on 2006-04-30
Yeah, I've restarted, it happens all the time, not just in the terminal...

---

### Post by henriquemaia on 2006-04-30
[QUOTE=gumbald]Yeah, I've restarted, it happens all the time, not just in the terminal...[/QUOTE]

Check under **gconf-editor** the metacity entry and its global_keybindings.

Maybe you have already tried that.

---

### Post by gumbald on 2006-04-30
That was a strange one, changed keyboard over from USB adapter to the PS2 port (long story) and all is fine!

Thanks anyway :)

---

