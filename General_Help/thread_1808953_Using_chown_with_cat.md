---
title: "Using chown with cat?"
date: 2011-07-21
forum: General Help
---

### Post by NormaJean on 2011-07-21
Ahoy!

I have a list specific list of dirs/files that need to be changed into another users name.

I initially thought that this would work:
chown -Rc user.name 'cat user.name1.txt' 

but I get 
chown: cannot access 'cat user.name1.txt No such file or directory

Any help is appreciated <3

---

### Post by idoitprone on 2011-07-21
```
chown -Rc user.name `cat user.name1.txt`
```

change the single quotes to the character above the tab then your script might work if the script is formatted properly

---

### Post by NormaJean on 2011-07-21
Ended up using xargs..

> cat user.user1.txt | xargs -I{} chown user.user {} 

---

