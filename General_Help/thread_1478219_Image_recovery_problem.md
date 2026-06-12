---
title: "Image recovery problem"
date: 2010-05-09
forum: General Help
---

### Post by BadlyNeedHelp on 2010-05-09
So I have just ran testdisk on my Camera, all is going well but I have looked in my home folder to get the folder of the recovered images, and I cant see to find it.

All I see is

photorec.ses with a padlock on, when I click it I get this

Could not display "/home/MY NAME/photorec.ses".

Why is this?

---

### Post by SPr on 2010-05-09
```

sudo chown -R MY_NAME\: ~/photorec.ses

```
You don't currently own the directory or files so you'll have to change the ownership of them.
```

ls -l photrec.ses

```
will show what I mean.

---

