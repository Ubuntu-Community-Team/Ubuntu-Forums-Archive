---
title: "Can't Delete folder"
date: 2010-07-21
forum: General Help
---

### Post by Punkristo on 2010-07-21
I created a folder and some how it is protect it and I can't get in it or delete it. The folder has this image:

[IMG]http://img4.imageshack.us/img4/3935/folderg.png[/IMG]

---

### Post by xpowerfulxx on 2010-07-21
Are you an admin on your computer?

---

### Post by AlphaLexman on 2010-07-21
In the parent directory, post the output of:
```
ls -l
```

---

### Post by rubylaser on 2010-07-21
I'll but you made the folder as the superuser.  Just open a terminal cd into the directory that holds that folder, and run

```
sudo chown -R yourusername:yourusername Lesya
```

Obviously replace the yourusername that's above with your actual username, so for my user it would look like this.


```
sudo chown -R rubylaser:rubylaser Lesya
```

Hope that helps.

---

### Post by Punkristo on 2010-07-21
> **rubylaser said:**
> I'll but you made the folder as the superuser.  Just open a terminal cd into the directory that holds that folder, and run

```
sudo chown -R yourusername:yourusername Lesya
```

Obviously replace the yourusername that's above with your actual username, so for my user it would look like this.


```
sudo chown -R rubylaser:rubylaser Lesya
```

Hope that helps.

Yep, that worked! Thanks a lot!

---

### Post by rubylaser on 2010-07-21
No problem, glad I could be of help :)

---

