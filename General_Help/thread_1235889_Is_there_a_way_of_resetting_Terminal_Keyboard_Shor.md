---
title: "Is there a way of resetting Terminal Keyboard Shortcuts back to default?"
date: 2009-08-09
forum: General Help
---

### Post by Dr. Lucien Sanchez on 2009-08-09
Hello there. I changed some of the keyboard shortcuts for the terminal (more precisely I changed Ctrl+C from Abort Command to Copy, because I'm a ******* knuckle-dragging simpleton). Now I've started using Mediatomb which kind of relies on having access to the Ctrl+C (Abort Command) shortcut. Now, when I try to set it back to what it was inside the terminal's Keyboard Shortcuts section there is no line for 'Abort Command' (or something along those lines). The same thing applies to 'System > Preferences > Keyboard Shortcuts' and the same for 'gconf-editor'

So basically what I'm asking for is: 'Is there a way of resetting Terminal Keyboard Shortcuts back to default?'

Cheers.

---

### Post by SuaSwe on 2009-08-09
How did you change the commands to custom in the first place?

---

### Post by SuaSwe on 2009-08-09
Never mind - I'm guessing you did it in Edit > Keyboard Shortcuts. :D

The only possibly relevant item I've found is the file /etc/inputrc . Can you see anything relevant in there? Meanwhile I'll keep looking and see what else I can find!

---

### Post by SuaSwe on 2009-08-09
Also, have you tried simply setting Copy back to Shift+Ctrl+C in Keyboard Shortcuts to see if Ctrl+C sets itself back to its default setting?

---

### Post by Dr. Lucien Sanchez on 2009-08-09
Excellent stuff! Just changing the command back to before solved the issue. Many, many thanks!

---

