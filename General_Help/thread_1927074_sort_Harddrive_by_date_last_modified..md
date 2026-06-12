---
title: "sort Harddrive by date last modified."
date: 2012-02-17
forum: General Help
---

### Post by conradin on 2012-02-17
Hi everyone!
I have an old windows hard-drive with potential interesting data on it. What I want to do is get a list of all the files on the hard-drive sorted by last modification data. Does anyone have an idea about how to make a script do that? I'm thinking the find command, but I'm only aware that the find command can do is date created....

---

### Post by Khayyam on 2012-02-17
> **conradin said:**
> I have an old windows hard-drive with potential interesting data on it. What I want to do is get a list of all the files on the hard-drive sorted by last modification data. Does anyone have an idea about how to make a script do that? I'm thinking the find command, but I'm only aware that the find command can do is date created

Well, find also has 'newer' '-newermt' (newer mtime) 'mtime'

```
find . -newermt "jan 03, 2012"
```

---

