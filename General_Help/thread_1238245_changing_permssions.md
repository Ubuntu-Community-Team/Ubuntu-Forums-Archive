---
title: "changing permssions"
date: 2009-08-12
forum: General Help
---

### Post by stmartin on 2009-08-12
Hello again!

I created one file called "test" and changed its permissions to -------rwx. It means that the owner and the owner group can't do anything, and all others can do everything :)

My user at the moment is "yas" and the owner group the same "yas". At this moment I can't operate with the file since I am the owner and I got 0 permissions.

So I did a little change. I made chown and chgrp to "ttt", so that the owner would be the group "ttt" and the user "ttt".

Now I can operate the file, or can I ?

I tried to open the file, and it opens. But the only problem is that it is read-only? How is that possible? I made rwx for all other users?

Thanks in advance.

Regards.

---

### Post by mikewhatever on 2009-08-12
Could it be that yas belongs to the ttt group?

---

### Post by stmartin on 2009-08-12
> **mikewhatever said:**
> Could it be that yas belongs to the ttt group?

Thanks for the reply.

No, not at all. Even if it was like that, I wouldn't have the right to read the file. So its not that case.

Regards.

---

