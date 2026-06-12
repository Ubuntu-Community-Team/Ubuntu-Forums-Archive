---
title: "missing trash directory"
date: 2011-07-07
forum: General Help
---

### Post by tachyon4 on 2011-07-07
The directories
/home/<user_name>/.Trash
and
/root/.Trash
do not exist.

I've tried viewing hidden directories with nautilus and using "cd" in terminal.  "locate" is equally useless.

---

### Post by Habitual on 2011-07-07
as the user:
```
find `pwd` -iname *Trash* -type d
```

root won't have a Trash folder if root has never logged into the desktop, I believe.

---

### Post by sisco311 on 2011-07-07
> **tachyon4 said:**
> The directories
/home/<user_name>/.Trash
and
/root/.Trash
do not exist.

I've tried viewing hidden directories with nautilus and using "cd" in terminal.  "locate" is equally useless.

It's under "$HOME/.local/share/Trash"

For more details, see:
[http://www.ramendik.ru/docs/trashspec.html](http://www.ramendik.ru/docs/trashspec.html)

---

### Post by tachyon4 on 2011-07-07
$HOME/.local/share/Trash

Yep.  Thanks!

---

### Post by sisco311 on 2011-07-07
You are welcome! 

Don't forget to mark this thread as SOLVED. Thanks!

---

### Post by 0z0ne on 2011-09-22
Hi, I'm having the same trouble, however i can't find a .local directory in my home folder.
I've tried the code suggested by Habitual:
find `pwd` -iname *Trash* -type dand get back:
[FONT=monospace]/home/owen/.gconf/apps/evolution/mail/trash
/home/owen/.local/share/Trash

..but I can't locate the folder.
What am I doing wrong?

Cheers

[/FONT]

---

### Post by sisco311 on 2011-09-22
> **0z0ne said:**
> Hi, I'm having the same trouble, however i can't find a .local directory in my home folder.
I've tried the code suggested by Habitual:
find `pwd` -iname *Trash* -type dand get back:
[FONT=monospace]/home/owen/.gconf/apps/evolution/mail/trash
/home/owen/.local/share/Trash

..but I can't locate the folder.
What am I doing wrong?

Cheers

[/FONT]

It's there, but hidden. You might have to press Ctrl+H in your file manager to list hidden files/directories.

---

### Post by 0z0ne on 2011-09-22
Aha!! It's there!!
Thanks Cisco,
much appreciated!
:)

---

### Post by sisco311 on 2011-09-22
You are welcome!

---

