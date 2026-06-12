---
title: "synaptic seems to be broken"
date: 2006-06-17
forum: General Help
---

### Post by oldmanstan on 2006-06-17
i have no idea what could have caused this but a few minutes ago i noticed that there seemed to be packages that should have been showing up in synaptic but weren't.

i figured that my sources.list file got changed somehow (i ran automatix a couple times so i thought maybe something happened). anyway, i went into the repositories menu in synaptic and the dialog box would appear for about half a second then disappear and i would get a message saying the repositories have changed and i have to hit refresh

i also tried the add/remove thing in the applications menu, it won't even load

any ideas? it doesn't seem like it's a sources.list problem at all

thanks

---

### Post by H.E. Pennypacker on 2006-06-17
Did you try removing what does not belong there in the sources list, and starting over?  

Do you get an error about broken packages?

---

### Post by oldmanstan on 2006-06-18
no broken packages message. one thing i noticed is that it doesn't seem to be accessing ANY repositories since when i click "all" to show all packages the number at the bottom that it says it is displaying is the same as the number installed

EDIT: oh wow, i went in and checked the sources.list file and found the problem... there was none! something (automatix?) removed it and forgot to put it back. There were several backups (probably from running automatix) so i restored one of them then checked it to make sure it was right

thanks for the help!

---

