---
title: "Nevermind :)"
date: 2009-09-01
forum: General Help
---

### Post by Bungo Pony on 2009-09-01
Feel free to delete. my bad

---

### Post by amauk on 2009-09-01
Use ```
cd network
```not ```
cd /network
```

```
/
|
|___/media
|      |
|      |___/media/network
|      |___/media/another_folder
|
|___/opt
      |
      |___/opt/folder-A
      |___/opt/folder-B
```

- You're in /media
- You change directory to /network (Ie. a directory called "network" directly below the root dir)
- /network doesn't exist
- mkdir network (Ie. make a directory, under current working directory, called "network")
- /media/network already exists

---

