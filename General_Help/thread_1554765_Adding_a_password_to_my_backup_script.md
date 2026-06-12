---
title: "Adding a password to my backup script"
date: 2010-08-17
forum: General Help
---

### Post by rogerdean on 2010-08-17
Hello all

I've been using tar in a small script to backup my stuff, like this...

```
tar -pczvf backup-`date +%Y-%m-%d`.tar.gz /home/roger/Desktop /home/roger/Documents /home/roger/.thunderbird
```

Now I'd like to switch to something that supports passwords, perhaps 7z or zip. 7z has better compression, right? Which is faster? Can anyone suggest how the line above should be modified?

Many thanks indeed
Roger

---

