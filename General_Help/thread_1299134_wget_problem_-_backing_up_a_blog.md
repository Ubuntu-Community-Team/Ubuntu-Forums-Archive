---
title: "wget problem - backing up a blog"
date: 2009-10-23
forum: General Help
---

### Post by raywood on 2009-10-23
I'm using this command to back up a private, passworded blog:

```
wget -mrc --convert-links --progress=dot --http-user=[user name] --http-password=[password] --level=3 --page-requisites --no-parent [URL]
```

That command gives me repeated instances of this:

```
Read error at byte 15928/15467 ((null)).  Retrying.
```

What's wrong with my command?

---

