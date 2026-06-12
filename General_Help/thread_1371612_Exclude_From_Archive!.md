---
title: "Exclude From Archive!"
date: 2010-01-03
forum: General Help
---

### Post by Chamillionaire2 on 2010-01-03
What's Up?

OK, So I'm trying to make an archive of a folder while trying to exclude some file extensions from it. Here's what I've been trying.
```
tar -zcvf mybackup.tar.gz --exclude='.js' folder
```

But it just archives the entire folder.

Anyone Know?

Thanks Bye.

---

### Post by Hellkeepa on 2010-01-03
HELLo!

Tried with this?
```
tar -zcvf myback.tar.gz --exclude='*js' folder
```

PS: This is not a programming question.

Happy syncin'!

---

### Post by Barriehie on 2010-01-03
> **Chamillionaire2 said:**
> What's Up?

OK, So I'm trying to make an archive of a folder while trying to exclude some file extensions from it. Here's what I've been trying.
```
tar -zcvf mybackup.tar.gz --exclude='.js' folder
```

But it just archives the entire folder.

Anyone Know?

Thanks Bye.

How about --exclude=*.js   without the quotes.

---

