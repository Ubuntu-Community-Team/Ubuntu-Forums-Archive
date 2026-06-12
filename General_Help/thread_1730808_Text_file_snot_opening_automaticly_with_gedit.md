---
title: "Text file snot opening automaticly with gedit"
date: 2011-04-16
forum: General Help
---

### Post by joelstitch on 2011-04-16
I have text files (.txt) to open with gedit but every time I try to open a text file it says:

```
Do you want to run "Installed programs", or display its contents?
```

And if I press Display it will open. How do I make it open automatically?

---

### Post by dino99 on 2011-04-16
when you right click on a file, you can choose to "edit with", select for example "gedit" and validate that choice as permanent (check the radio box)

---

### Post by WorMzy on 2011-04-16
You are getting that message because the text file "Installed programs" is executable. One solution is to remove the executable bit from the file by right-clicking the file, choosing Properties, switching to the Permissions tab, and unchecking the "Allow executing file as a program" box (or by running chmod -x on the file from the terminal).

[IMG]http://img20.imageshack.us/img20/4241/71903599.png[/IMG]

Another solution is to disable the prompt, and have nautilus either open all executable text files for editing automatically, or have them run as an application automatically. To set this, open Nautilus and go to Edit -> Preferences -> Behaviour, and look under "Executable Text Files".

[IMG]http://img171.imageshack.us/img171/6404/86289194.png[/IMG]

The only other solution (AFAIK) is to use a different file browser. However, other file browsers may behave in the same way.

---

### Post by joelstitch on 2011-04-16
> **WorMzy said:**
> You are getting that message because the text file "Installed programs" is executable. One solution is to remove the executable bit from the file by right-clicking the file, choosing Properties, switching to the Permissions tab, and unchecking the "Allow executing file as a program" box (or by running chmod -x on the file from the terminal).

[IMG]http://img20.imageshack.us/img20/4241/71903599.png[/IMG]

Another solution is to disable the prompt, and have nautilus either open all executable text files for editing automatically, or have them run as an application automatically. To set this, open Nautilus and go to Edit -> Preferences -> Behaviour, and look under "Executable Text Files".

[IMG]http://img171.imageshack.us/img171/6404/86289194.png[/IMG]

The only other solution (AFAIK) is to use a different file browser. However, other file browsers may behave in the same way.
That did it. Thanks!

---

