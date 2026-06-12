---
title: "&quot;mount: No such file or directory&quot;"
date: 2011-02-22
forum: General Help
---

### Post by Rodayo on 2011-02-22
Trying to run this command
```
mount -o bind /git /path/to/file/git/
```

I get this error. 
> mount: No such file or directory

Both /git and /path/to/file/git exist. I am 100% sure of that. But other that the error puzzles me...

Any ideas?

Edit: turns out it was already mounted, hence the error. Although I would've expected a message like "/git is already mounted"

---

