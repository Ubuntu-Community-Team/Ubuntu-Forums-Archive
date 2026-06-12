---
title: "Mass regex search/replace without changing files"
date: 2011-01-10
forum: General Help
---

### Post by saverio.miroddi on 2011-01-10
I need to do a regex search/replace in multiple files.

Now, I found two general solutions:

- find+perl/ruby
- awk s/.../gwp

but both seem to change the files metadata even if nothing has been changed - this is a problem, since other programs may rely on the change date for several reasons (e.g. SCMs will have to rescan the files) - I guess they also rewrite the files.

Is there a way to mass regex search/replace, without writing to the unchanged files?
I can write a script, but I would be curious if there is a more standard way.

Thanks!

---

