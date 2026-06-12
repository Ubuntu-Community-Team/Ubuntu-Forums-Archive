---
title: "Symbolic link with date Variable"
date: 2009-10-16
forum: General Help
---

### Post by frisbie on 2009-10-16
Firstly, it is my first post here, so, hello. :)

Now, I wonder, if there is an option to create sym link with a variable, but in the time of calling original file not creating symlink (ln -s `date +%Y.%m`.log logs).

As you can see, I would need that so log file would always link to current month log file. I can rebuild links with cron every month, but I think there should be a better solution.

Any hints are welcome.


Thanks.

---

### Post by Bachstelze on 2009-10-16
> **frisbie said:**
> Now, I wonder, if there is an option to create sym link with a variable, but in the time of calling original file not creating symlink

Wat?

---

### Post by frisbie on 2009-10-16
> **Bachstelze said:**
> Wat?
Same symlink links every month to a different file.

Example:
- october 2009 to 2009-10.log
- november 2009 to 2009-11.log
- december 2009 to 2009-12.log
- ...

---

