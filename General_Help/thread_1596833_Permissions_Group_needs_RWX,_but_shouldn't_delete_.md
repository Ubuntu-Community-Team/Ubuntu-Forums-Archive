---
title: "Permissions: Group needs R/W/X, but shouldn't delete files they do not own"
date: 2010-10-14
forum: General Help
---

### Post by pbwalker on 2010-10-14
I've got, what has become to me, a brain bender. It seems ACL's are the best way to go, but I am not 100% sure.

Each user should be able to create files and modify each others' files, but should not be able to delete any one else's files in a directory.

chmod -1777?
setfacl?

Now, I know with modify, they can delete. But to be honest, that's fine. I just need to prevent them from rm-ing a file (unless they are the owner)

:confused:

---

