---
title: "Passing parameters from Nautilus to an arbitrary script"
date: 2011-06-28
forum: General Help
---

### Post by construKction on 2011-06-28
Greetings,

I would like to write a script which would enable me to do following actions
  - select certain files in Nautilus
  - type in a keyboard shortcut which would run my script
  - do something intelligent with selected files 

Let's say that this 'intelligent' work is for starters to open new terminal window in the present location and list the selected files.

What I ask is this: How do I pass on my current location in the file system and a list of selected files via described pathway so I can position myself and iterate over selected files?
Is there some other, more elegant way of achieving the same result (assuming I have imagined the workings of this type of thing correctly)?

---

### Post by Bachstelze on 2011-06-28
nautilus-actions lets you do almost the same thing, the difference being that the script would be run from the right-click menu. There might be a way to run with a shortcut, though, not sure.

---

### Post by construKction on 2011-06-28
> **Bachstelze said:**
> nautilus-actions lets you do almost the same thing, the difference being that the script would be run from the right-click menu. There might be a way to run with a shortcut, though, not sure.

Yes, I have added some scripts to .gnome2/nautilus_scripts and have explored options of the right click menu :), but I would like to know if there is a way of passing those arguments directly to my script?

---

### Post by Bachstelze on 2011-06-28
When you have files selected and run a script via nautilus-actions, the filenames will be passed as arguments to your script (it is then your script's job to parse them and take the appropriate action).

---

### Post by construKction on 2011-06-28
But is this not true only if I use the Nautilus pop up menu (right click)?

Being very scant on mouse clicks, and because I am writing a script that should be entirely to my liking and would serve for me to make my OS as easy to use and comfortable as possible, I would like to circumvent this.

So, is there  any way to employ the existing artillery to use a keyboard shortcut for the same purpose?

---

