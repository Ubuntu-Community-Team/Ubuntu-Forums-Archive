---
title: "Remove annoying warning when opening text files?"
date: 2010-06-20
forum: General Help
---

### Post by benjorino on 2010-06-20
I really hate this warning when I try to open certain types of files in gedit: (using ubuntu lucid)

> Do you want to run File.c or display its contents?

"File.c" is an executable text file.

Open in Terminal; Display; Cancel; Run

Is there any way to remove the warning? I have never once clicked anything other than display, and when I'm opening lots of files, having to hold down ALT-D to get rid of these warnings is becoming a pain!

Many thanks,
Ben

---

### Post by howefield on 2010-06-20
Right click the file > Permissions tabs > uncheck "Allow executing file as program" and close.

---

### Post by benjorino on 2010-06-20
> **howefield said:**
> Right click the file > Permissions tabs > uncheck "Allow executing file as program" and close.

That's helpful thanks!
Is there a way to make this the default behaviour (ideally for all text files not ending in .sh) ?

---

### Post by yetiman64 on 2010-06-20
Another way is in any nautilus window go to Edit > Preferences > Behaviour Tab, under "Executable Text Files", set to "View executable text files when they are opened". 

This has the advantage of not changing the files permissions.

---

### Post by ajgreeny on 2010-06-20
The possible problem with benjorino's solution is that some plain text files may need to be executable even though they are not .sh files. files, so you could find that some things don't work any more as they should.

However, if you do what yetiman64 says you will need to add another item to the "Open with" options tab, ie add **bash** to the applications listed when you right click.  If you do not do that you will never be able to run a .sh script from nautilus, which can sometimes be very useful.

---

### Post by yetiman64 on 2010-06-20
> ..add **bash** to the applications listed when you right click... Very good point, thanks ajgreeny. Usually only ever fire up scripts from terminal (~/bin folder & in $PATH) myself :).

---

### Post by benjorino on 2010-06-20
Thanks guys, that's perfect!
:grin:

---

