---
title: "i downloaded somethign. it is locked. cannot delete."
date: 2010-10-25
forum: General Help
---

### Post by Blackknite on 2010-10-25
hi i have downloaded something i didn't want. it is a book of like .mxl or something. this is a break down of the book but not the text file. i tried to delete it but it said i do not have permission. i am not the creator of this file. and so i cannot move it to the trash folder. any idea of how to delete this.

-move to trash-

-Cannot move file to trash, do you want to delete immediately?
The file "BOOK" cannot be moved to the trash.-

-Yes-

-Error while deleting.
There was an error deleting chapter01.
Error removing file: Permission denied-
(and so on for all 12 chapters)-

---

### Post by the8thstar on 2010-10-25
Get into the terminal and type at the prompt:

> sudo -i
(enter your password)

Then type

> rm 

Don't press enter yet... Select with your mouse the file you mentioned and drag it into the terminal window.

Now press enter. That should take care of things.

---

### Post by sikander3786 on 2010-10-25
You need to be careful with the ```
sudo -i
``` command. It will assume that you are root and you know what you are doing so be a lot careful.

Graphical method,

```
gksu nautilus
```

Navigate to the path and delete.

---

### Post by the8thstar on 2010-10-26
> **sikander3786 said:**
> You need to be careful with the ```
sudo -i
``` command. It will assume that you are root and you know what you are doing so be a lot careful.

Good call, Sikander. gksudo is a better failsafe in this aspect.

---

