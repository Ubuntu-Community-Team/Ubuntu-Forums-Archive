---
title: "Mutt not handling mailto: URLs"
date: 2010-12-10
forum: General Help
---

### Post by nukeqler on 2010-12-10
Ubuntu Lucid amd64, mutt-1.5.20-7ubuntu1

I'm pretty sure the following used to work:

```
$ mutt mailto:dumbemail@mailinator.com?subject="Whoop dee doo"
```

Now mutt exits silently with status=1.  Tried setting EDITOR/VISUAL, no difference.

Any ideas?

Edit:  I had tempdir pointed at a non-existent directory in my .muttrc.  Still annoying that there was no error message, but at least things are working again.

---

### Post by nukeqler on 2011-01-05
> **nukeqler said:**
> Ubuntu Lucid amd64, mutt-1.5.20-7ubuntu1

I'm pretty sure the following used to work:

```
$ mutt mailto:dumbemail@mailinator.com?subject="Whoop dee doo"
```

Now mutt exits silently with status=1.  Tried setting EDITOR/VISUAL, no difference.

Any ideas?

Anyone?  Bueller?  Mr. Beardsley?  Chief?  McCleod?

---

