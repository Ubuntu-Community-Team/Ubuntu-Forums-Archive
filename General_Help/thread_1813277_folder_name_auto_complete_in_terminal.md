---
title: "folder name auto complete in terminal"
date: 2011-07-27
forum: General Help
---

### Post by jon23d on 2011-07-27
In older versions of ubuntu I could use tab to autocomplete folder names multiple times in one command in a terminal, for example:

```
tar -cvf myapp.tar --exclude='/var/www/f[TAB]older-name/cache/*' --exclude='/var/www/f[TAB]older-name/sessions/*' /var/www/f[TAB]older-name

```

Now only the first tab works, is there any way to get this behavior back?

Thanks!

---

### Post by turtle153 on 2011-07-27
I never used it to that extent in earlier versions, but try your command again without the quotes on the filenames, and you should be able to use tab on the second filename. You only need to use quotes if there are spaces in the path.

---

### Post by jon23d on 2011-07-27
Thanks, that worked perfectly!

---

