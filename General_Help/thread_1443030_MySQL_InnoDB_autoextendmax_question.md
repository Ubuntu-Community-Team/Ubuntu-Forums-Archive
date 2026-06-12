---
title: "MySQL InnoDB autoextend:max question"
date: 2010-03-30
forum: General Help
---

### Post by bwitherell on 2010-03-30
Say i have this line in my my.cnf file
```
innodb_data_file_path=ibdata1:10M:autoextend:max:1000M
```

can anyone tell me what happens when ibdata1 reaches the maximum size of 1000M?

Does it break?
Does it not allow writes?
Does it delete old data?

I searched everywhere online for answers and came up empty handed.

Sorry, i know this is not an Ubuntu question but rather a MySQL question. It is running on an Ubuntu Server though :D

Anyway, Any help is much appreciated. I know there is someone here who knows the answers to these questions.

Thanks in advance!

---

### Post by bwitherell on 2010-04-21
When the DB reaches the max size it does not allow any more writes to it.

---

