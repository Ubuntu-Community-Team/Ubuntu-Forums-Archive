---
title: "Gnome-about-me not working"
date: 2010-11-29
forum: General Help
---

### Post by inameiname on 2010-11-29
All of a sudden I cannot run the 'About Me' under Applications -> System -> Preferences. I learned it can be run through the terminal using 'gnome-about-me', and after trying that, I get this error:

```

gnome-about-me

(gnome-about-me:12785): libebook-WARNING **: e-book.c:2245: cannot get book from factory: Invalid source

(gnome-about-me:12785): libebook-WARNING **: e-book.c:2245: cannot get book from factory: Invalid source

about-me-properties-ERROR **: Invalid source
aborting...
Aborted

```

Anybody ever got this? 

My big issue now is I just restored my computer and because I cannot open 'About Me', I cannot change my user password.

---

### Post by inameiname on 2010-11-29
Bump.


UPDATE:

Well, I found this, to change the user password. But that still doesn't explain why I'm now having this issue:

> 
Assuming you're just changing your own password, you can use the command naked:

 	Code:
 	passwd 
If you are wanting to change another user's password, you'll need to be a sudoer:

 	Code:
 	sudo passwd 
You should be prompted for the new password, twice.


---

### Post by inameiname on 2011-06-18
This was fixed for me ever since I installed Natty. Thus, while its not technically 'fixed', I'll still mark this issue as solved. Still curious as to why the issue occurred in the first place. Oh well.

---

