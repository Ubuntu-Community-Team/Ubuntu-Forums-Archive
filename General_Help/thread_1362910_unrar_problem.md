---
title: "unrar problem"
date: 2009-12-23
forum: General Help
---

### Post by Shamsul007 on 2009-12-23
basically i have rar file in parts, 16 total, the packaged file inside is 4.4gb, however when i extract it, the file extracted is around 2 gig. its an iso file, and i dont want to burn it without knowing it works.

---

### Post by oakgrove on 2009-12-23
```

$ mkdir temp
$ sudo mount extracted.iso temp -o loop -t iso9660

```
If it mounts successfully and you can browse it then it's okay.

---

### Post by Shamsul007 on 2009-12-23
okay ive just realized, it goes up to part 7 and then goes back to part 1 and asks for the password, why cant it extract all?

---

### Post by oakgrove on 2009-12-23
I'm sure you know, usually the way it works is there is one main rar file you click to extract and it just extracts the rest with it and reconstitutes the iso file or whatever that is in it back together from the pieces automatically.  I'm not sure exactly what you have going on there but, I'd just click on the file that looks like the main one and let it come up in the archive manager and just extract it using the archive manager's menus.  If the file you click isn't showing a 4.4 GB iso file in it, just exit out of that one and click on the other ones until it does.

---

