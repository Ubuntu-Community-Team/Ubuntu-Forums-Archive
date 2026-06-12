---
title: "Prompt for man Section"
date: 2010-02-12
forum: General Help
---

### Post by dambrown on 2010-02-12
I have another machine running openSUSE, which prompts for the man section if more than one manpage with that name exists.  Is there any way to make the version of man that Ubuntu has do this?  For example if I run 'man write', I want a prompt to let me view the manpage in section 2 instead of silently defaulting to section 1.

---

### Post by gmargo on 2010-02-12
I don't see any man option on Ubuntu to do that.  Since you've got it right there, what package does openSUSE use to provide the man command?

---

### Post by gmargo on 2010-02-12
I fired up my openSUSE 11.2 virtual machine and figured out what's going on.

Ubuntu Karmic's "man-db" package is man-db-2.5.6.
openSUSE's "man" package is actually man-db-2.5.2, with an additional patch to add the feature you described.

It is most likely possible to apply that patch (or similar) to the Ubuntu source code, but that is left as an exercise for the reader :D

---

### Post by dambrown on 2010-02-12
It does appear that the mod is a SUSE-specific thing.  I guess I'll just have to remember/repeatedly guess what section the appropriate manpage is in.

---

### Post by m_duck on 2010-02-12
Does something like this work:```
man 2 write
```

---

### Post by dambrown on 2010-02-12
That works, it's just near-impossible to guess if they put something in section 2, 3, or 7.

---

