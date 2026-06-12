---
title: "CLI - &quot;find&quot; - Hiding the annoying &quot;Permission Denied&quot; ?"
date: 2009-09-26
forum: General Help
---

### Post by rob86 on 2009-09-26
Is there a way to hide the huge amount of /file/file/file FILE "Permission Denied" stuff  when using "find /" ? I want to search my entire file system sometimes, but I never get the results because the logs full of files that say P.D. I guess I could use grep to filter that out, but I'm wondering if theres an option in the find command to do it.

---

### Post by LoneWolfJack on 2009-09-26
```
sudo find...
```

simple logic is the best... ;-)

---

### Post by kerry_s on 2009-09-26
> **rob86 said:**
> Is there a way to hide the huge amount of /file/file/file FILE "Permission Denied" stuff  when using "find /" ? I want to search my entire file system sometimes, but I never get the results because the logs full of files that say P.D. I guess I could use grep to filter that out, but I'm wondering if theres an option in the find command to do it.

yeah, you should use grep.
is there a reason you use "find /" instead of narrowing it down, for example "find /usr/", i mean why bother looking where you don't need to? the file system is pretty simple, certain things are only in certain places.

---

### Post by rob86 on 2009-09-26
I had thought about using sudo, but I remembered that it's often said to be bad practice being in sudo mode all the time. I was thinking there might be a way to just hide the permission denieds, instead of gaining permission.

---

### Post by nothingspecial on 2009-09-26
Sudo gives you permission.

Using sudo is perfectly fine as long as you know exactly what the stuff after it is going to do.

---

