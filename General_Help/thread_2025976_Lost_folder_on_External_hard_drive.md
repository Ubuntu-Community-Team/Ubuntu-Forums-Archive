---
title: "Lost folder on External hard drive"
date: 2012-07-14
forum: General Help
---

### Post by Toriam on 2012-07-14
I've lost a very large, important folder on my 1 TB external hard drive. I've searched a bit manually, started with photorec, and I'm not sure what would be easiest. I don't know how long it's been gone since there is so much info on there.Before I pull my hair out I thought I'd ask. What's the best way to search a huge external for a folder of photos, videos and graphics? I don't even remember what exactly I titled it, Graphics or Photos or something.

---

### Post by Sealbhach on 2012-07-14
I find the *locate* command very useful. First, update the file database

```
sudo updatedb
```

then run

```
locate filename
```

Where filename is the name (or part of the name) of the file you are looking for.

.

---

