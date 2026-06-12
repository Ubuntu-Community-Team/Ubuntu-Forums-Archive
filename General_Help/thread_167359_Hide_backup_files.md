---
title: "Hide backup files"
date: 2006-04-28
forum: General Help
---

### Post by jonnymccullagh on 2006-04-28
When I edit files I get backup files e.g.
myfile.htm
myfile.htm~

This is beginning to annoy me - can I stop the backups from being made?
Thanks,
jonny

---

### Post by tenn on 2006-04-28
If you are using Kate there is a selection in the options to stop it making back ups I don't have Kate installed so I don't know the excact options.

---

### Post by aysiu on 2006-04-28
Go to **Configure Kate** (I think it's under **Settings**) and under the save thing, instead of making backup files appended with ~, make them prefixed with . instead

That way, it'll be this:
filename
.filename

instead of this:
filename
filename~

Files with a . at the beginning are hidden files.

---

### Post by jonnymccullagh on 2006-05-02
thanks - that has sorted it,
I also had to stop Bluefish from making the backups too.
Cheers,
jonny

---

