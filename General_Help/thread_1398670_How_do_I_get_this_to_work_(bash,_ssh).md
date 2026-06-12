---
title: "How do I get this to work? (bash, ssh)"
date: 2010-02-04
forum: General Help
---

### Post by The Switch Blade on 2010-02-04
I'm ssh'ed into my school servers. I want to do

"emacs combo.c &"

where combo.c is a c program.

All I see is:

[3] 12979

and I've tried this 3 times... so I think I opened 3 processes, but I don't see them over here :(

---

### Post by Bachstelze on 2010-02-04
You don't want the ampersand at the end. It tells the program to run in the background, which is why you're not seeing it.

---

### Post by gmargo on 2010-02-04
[QUOTE=]I've tried this 3 times... so I think I opened 3 processes, but I don't see them over here [/QUOTE]

Assuming you're using the bash shell, use a "jobs -l" command to see the processes that are currently running the background.  Use a "fg" command (or "fg" followed by a number to choose from several) to bring the command to the foreground.

---

### Post by The Switch Blade on 2010-02-04
Okay, cool, thanks. When I am on the school computers, doing the "&" makes it appear in a new window. Is there a way for the emacs editor to open up in a new window when going through bash/ssh?

---

### Post by t4thfavor on 2010-02-04
You can use screen, if its installed by screen emacs program.c then you can detach it and use other programs.

type screen -r to reconnect.

---

### Post by dstein on 2010-02-04
You can also run ssh with the -X option to enable X11 forwarding. This way, X will be enabled and emacs will open in a new window. Without X11 forwarding, I believe that running emacs is equivalent to running `emacs -nw', which is the no window option.

---

