---
title: "Import personal GPG key in Seahorse"
date: 2012-06-29
forum: General Help
---

### Post by Carborundum on 2012-06-29
I want to transfer a GPG key that I occasionally use to sign emails from one computer to another. Seahorse allows exporting and importing of keys, but when I try to import the key it becomes public instead of private. As a result, I can't use it to sign anything.

How can I import the file in such a manner that the key becomes private instead of public?

---

### Post by Carborundum on 2012-07-08
I figured it out. As far as I can tell, this is not possible to do from the GUI. Instead, I had to run the following from a terminal:

```
gpg --export-secret-keys -a "<Key>" > private.key
```This exports the personal key <Key> to the file 'private.key'. This can then be moved to the target computer and imported with:
```
gpg --allow-secret-key-import --import private.key
```Now, from what I can discern from the man page for gpg, this is not really how things are supposed to be done. --export-secret-keys is said to be "not very usefull", as well as being a "security risk". --allow-secret-key-import is said to be "obsolete". Nevertheless, this works, and I haven't been able to find a better way to accomplish this. Perhaps I just don't understand how gpg keys are meant to be used.

---

### Post by chrisinspace on 2012-10-29
Thanks for posting this.  It was exactly what I was looking for.  Worked perfectly.

---

