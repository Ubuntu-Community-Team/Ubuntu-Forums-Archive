---
title: "How do I get write permission to a directory?"
date: 2010-02-21
forum: General Help
---

### Post by litlfrog on 2010-02-21
I tried to read the File Permissions page on the wiki and my eyes glazed over after about three sentences. I've got a folder called /var/www/pics that I just want to be able to save image files to. My only other choice as I understand it is to save them to my home folder, then use a "sudo mv" command to copy files to that directory. How do I give my account permissions to save a file in that directory?

---

### Post by LoneWolfJack on 2010-02-21
you can either fiddle with user groups or grant write access to all users:

```
chmod 0777 /folder/name
```

---

### Post by jamesisin on 2010-02-21
You probably don't want to change permissions under /var/www/ because you want root to manage those contents.

You are better off using either sudo mv or sudo cp (move or copy) to generate the content you want in that folder.

You could create a special folder under your home directory (or elsewhere) that contained a script which copied or moved any .jpg file (for instance) which you placed into it to that location.  Or a script which you ran manually which did the same for any .jpg files located in that directory.  (Keep in mind the automatic script would be a security risk.)

---

