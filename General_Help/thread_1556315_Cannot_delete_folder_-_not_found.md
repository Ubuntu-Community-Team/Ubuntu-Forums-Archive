---
title: "Cannot delete folder - not found"
date: 2010-08-19
forum: General Help
---

### Post by b0wter on 2010-08-19
I've got a folder on my disk that I simply cannot interact with at all. It was created while extracting an archive. It has a special character in its name: "ä". But all those other characters work fine. Can anyone give me a hint on how to delete the folder?

Tried in terminal with rm -r which gives me an error:

```

rm: cannot remove `03 - Und die unertr_glichen Schmuggler/': No such file or directory

```

---

### Post by b0wter on 2010-08-19
Forgot to mention it, but I tried deleting it with nautilis which didnt work either. The file is on a network pc which I connect to via CIFS.


EDIT:
I found a somewhat strange solution to my problem... I connected to the share with a windows machine and was able to successfully delete the folder.

---

