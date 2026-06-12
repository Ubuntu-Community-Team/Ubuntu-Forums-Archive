---
title: "Hidden directory on ext3 drive"
date: 2010-08-24
forum: General Help
---

### Post by Spice Weasel on 2010-08-24
I have recently reformatted my external hard disk to ext3, and now whenever I delete something via my file manager, a hidden directory (".Trash-1000")  is made. I would like to keep this drive clean, is there any way to stop the directory from being made? I'm getting annoyed having to rm -r it every time I delete something.

I am using Thunar if that helps.

---

### Post by Intrepid Ibex on 2010-08-24
It is what is says it is: it's a trash. The "1000" part means it's for the group "1000" being the first user created (that being the _your_ user).

If you want it not to be created you can just use 'Shift + Delete' when deleting files to bypass them from being sent to the trash can.

---

### Post by WorMzy on 2010-08-24
Recursively chowning that directory as root, or chmodding it so that you don't have write rights may prevent files being sent there when deleted, and will probably tell you when you're deleting things on that partition that the can't be sent to trash, but you can delete them permanently.

So:
```
chown -R root:root /path/to/.Trash-1000
```
or
```
chmod ug-w /path/to/.Trash-1000
```

---

### Post by Spice Weasel on 2010-08-24
> **Intrepid Ibex said:**
> It is what is says it is: it's a trash. The "1000" part means it's for the group "1000" being the first user created (that being the _your_ user).

If you want it not to be created you can just use 'Shift + Delete' when deleting files to bypass them from being sent to the trash can.

Thanks, this works.

---

