---
title: "Remove symbolic link?"
date: 2006-05-28
forum: General Help
---

### Post by _simon_ on 2006-05-28
How do I remove one?

Trying to "delete" it does not work.

---

### Post by meng on 2006-05-28
You mean that you tried "rm"? because "delete" is not a standard command.

---

### Post by Titus A Duxass on 2006-05-28
Try from the CLI -sudo rm "name-of-link"

---

### Post by _simon_ on 2006-05-28
sorry yes i tried rm from terminal and delete via nautilus.

---

### Post by _simon_ on 2006-05-28
```

simon@ubuntu:~$ sudo rm /home/simon/delete/libjavaplugin_oji.so
rm: cannot remove `/home/simon/delete/libjavaplugin_oji.so': No such file or directory

```

I can see it in nautilus but if I do ls in the directory it doesn't display anything?

lol now I'm confused, I just used reload in nautilus (again) and now the file has gone!

It must be nautilus playing up. I just tried to delete the "delete" directory but it wouldn't let me, I had to do it via terminal.

All sorted now - thanks for your help.

---

### Post by meng on 2006-05-28
Something funny going on here. I tried rm to remove a symbolic link and it worked fine.

---

