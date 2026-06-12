---
title: "&quot;Tree&quot; command outputs odd characters"
date: 2011-03-15
forum: General Help
---

### Post by ondemanddesign on 2011-03-15
When I use the command "Tree" I am presented with odd characters. Is there a setting to change this to a more appealing character set or do I just have to deal with this?

```
ubuntu@ubuntudev:~$ tree
.
âââ backups
    âââ backup.fsa

```

The odd characters are the "â"'s

Thanks.

---

### Post by Old *ix Geek on 2011-03-15
In my terminal, Konsole, right-click brings up a "set encoding" choice on its menu. If your terminal has similar functionality, check there, or check within its settings.

---

### Post by ondemanddesign on 2011-03-15
> **Old *ix Geek said:**
> In my terminal, Konsole, right-click brings up a "set encoding" choice on its menu. If your terminal has similar functionality, check there, or check within its settings.

I am using PuTTY to SSH into my machines, I can not find any encoding functionality within it.

---

### Post by _0R10N on 2011-03-15
You could try running it with -A swith

```
tree -A
```

That will give your output a nice formatting.

For more switches and options, check this link

[http://www.computerhope.com/unix/tree.htm](http://www.computerhope.com/unix/tree.htm)

---

### Post by ondemanddesign on 2011-03-15
Thanks. That worked. This is solved.,

---

### Post by minja on 2012-08-25
Thanks, that worked

---

