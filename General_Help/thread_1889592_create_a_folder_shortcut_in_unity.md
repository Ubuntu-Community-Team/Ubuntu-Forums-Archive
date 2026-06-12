---
title: "create a folder shortcut in unity?"
date: 2011-12-01
forum: General Help
---

### Post by onesojourner on 2011-12-01
I need to add some folder shortcuts in unity. the folders are mounted at file system /1storage , /2storage ect.

---

### Post by jjex22 on 2011-12-01
Hi there do you mean symlinks? if so you just use the ln command from terminal, see [ehow]("http://www.ehow.com/how_8130731_create-symbolic-ubuntu.html") for an example :)

Hope it helps, if I misunderstood, please correct me!

---

### Post by efflandt on 2011-12-01
Explain what you mean by "folder shortcut".

If you open a partition in the folder viewer (top left) which automounts it, you can right click it in the left panel and click "Add Bookmark" to add it to your list of folders under "Computer", and/or you can right click it in the Unity bar and select "Keep in launcher".

Follow jjex22's reply if you want the partition (or folder or file on it) to also appear to be somewhere else on your file system (even under a different name) with a symlink (ln -s, see **man ln**).

---

