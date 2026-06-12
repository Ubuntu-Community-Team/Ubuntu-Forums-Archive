---
title: "recovering deleted files"
date: 2010-01-03
forum: General Help
---

### Post by dink123 on 2010-01-03
hi everyone,
i want to know how can i recover deleted files in ext3 partition manually(not using any tools)?? probably using the 'grep' command. if someone know pls tell me...

(i have recoverd deleted files in an ext2 partition with debugfs and dump . but dumping doesnt work for ext3)

Thank you guys for any help..

---

### Post by danastasio on 2010-01-03
its not possible to recover files deleted with an ext3 file system. Unlike windows, where files basically go to a hidden folder, if you delete a file in linux, its gone forever.

---

### Post by dink123 on 2010-01-03
actually u cant say impossible to retrive data as the contents of the data blocks are not really deleted.

below is something i found upon my searchin,
"...There has always been a misconception that such files cannot be retrieved in ext3. In fact, it is quite possible to retrieve the data..."

---

### Post by oldos2er on 2010-01-03
You could try Photorec: [http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

It's part of the Testdisk package.

---

### Post by dink123 on 2010-01-03
hey im sorry..but i want to do it manually as i said 'coz this is kind of a learning activity.

---

