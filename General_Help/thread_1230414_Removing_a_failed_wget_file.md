---
title: "Removing a failed wget file"
date: 2009-08-03
forum: General Help
---

### Post by TuckLive on 2009-08-03
I have a file called index.html?url=www.ossec.net%2Ffiles%2Fossec-hids-2.1.1.tar.gz&servfail.  This was a result from a failed wget command.  I get no file or directory found when I try sudo rm.

Since it's not picked up as a file I can't change permissions.  The only way I know how to remove this file is to ssh with a gui as root, but I don't want to give root a password.  Is there another way to remove this?  This is Server Edition so command line only.

---

### Post by credobyte on 2009-08-03
Try:
```
sudo rm -r "index.html?url=www.ossec.net%2Ffiles%2Fossec-hids-2.1.1.tar.gz&servfail"

```

---

### Post by renkinjutsu on 2009-08-03
the file has to be there.. just tab-autocomplete it..

make sure the file even exists first
do something like
ls -a | grep index

---

### Post by TuckLive on 2009-08-03
> **credobyte said:**
> Try:
```
sudo rm -r "index.html?url=www.ossec.net%2Ffiles%2Fossec-hids-2.1.1.tar.gz&servfail"

```

That worked.  Thanks

---

