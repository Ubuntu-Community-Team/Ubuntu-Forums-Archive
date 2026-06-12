---
title: "Bizarre error with ls"
date: 2010-06-16
forum: General Help
---

### Post by WebDrake on 2010-06-16
I'm having the most strange and bizarre error when using the ls command.

Regular ls works fine, but (in my home directory) when calling [FONT="Courier New"]ls *[/FONT] (or any other filter for the filename) I get an error message:
```
ls: invalid option -- 'z'
Try `ls --help' for more information.
```

I don't get this error in subdirectories.

Any idea what is happening?

Thanks & best wishes,

    -- Joe

---

### Post by WebDrake on 2010-06-16
Reason found -- a filename beginning with a hyphen. ](*,)

---

