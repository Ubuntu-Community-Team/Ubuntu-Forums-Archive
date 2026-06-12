---
title: "deleted passwd"
date: 2010-04-25
forum: General Help
---

### Post by akshayy on 2010-04-25
I accidentally deleted /etc/passwd while i was scripting something
but I found out there was an exact copy of that file in /etc/passwd-

The powerful server had 9 users and it would have been a terrible disaster !

I want to know from where did this /etc/passwd- file come from ?!! mark this thread as solved only after we get the answer to this question.
Its Ubuntu Server 9.10 btw !! 

Regards.

---

### Post by _0R10N on 2010-04-25
Think of that file as a backup copy that the OS creates when editing or deleting files. If you want to see this in action, try the following:

```

gedit /tmp/mytestfile

```

Write anything on it, save, and close. Then
```

ls /tmp

```
You'll see that there's only a mytestfile file, not a mytestfile~ (yet). Now, again
```

gedit /tmp/mytestfile

```
again, write anything on it, save, and close. Then
```

ls /tmp

```
And there it is!!!

Remember, it's just a backup copy, like the .bak that Windows handles.

Kind regards!

_0R10N >>

---

### Post by _0R10N on 2010-04-25
One more thing, this behavior can be a little annoying when working against a central server, like a SVN repository, so if you want to get rid of them, just
```

find <your_folder> -name '*~' | xargs rm

```

Kind regards!

_0R10N >>

---

