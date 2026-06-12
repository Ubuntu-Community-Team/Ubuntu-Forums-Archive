---
title: "chmod  to destroy my os?"
date: 2011-05-17
forum: General Help
---

### Post by luofeiyu on 2011-05-17
in my terminal :
sudo chmod 700 /home
now ,i can not enter my os.when i open os :
could not update iceauthority file /home/pt/.iceauthority.
how can i do?

---

### Post by mikewhatever on 2011-05-17
Playing with chmod is not a good idea. Not saying you shouldn't, but yes, it can break the system beyond repair.
You should be able to boot into recovery mode and use the following commands to restore the original permissions:
```
chown pt:pt /home/pt/.ICEauthority

chmod 600 pt:pt /home/pt/.ICEauthority
```

Note that Linux shell is case sensitive, so that 'ICEauthority' and 'iceauthority' are not the same.

---

### Post by Lars Noodén on 2011-05-17
> **luofeiyu said:**
> in my terminal :
sudo chmod 700 /home
now ,i can not enter my os.when i open os :
could not update iceauthority file /home/pt/.iceauthority.
how can i do?

Change it back to 755.
```

sudo chmod 755 /home

```

---

### Post by Rubi1200 on 2011-05-17
You should also take a look at the following links for more information on what went wrong and how to fix it:
[http://ubuntuforums.org/showpost.php?p=6138880&postcount=1](http://ubuntuforums.org/showpost.php?p=6138880&postcount=1)
[https://help.ubuntu.com/community/dmrcErrors#preview](https://help.ubuntu.com/community/dmrcErrors#preview)

---

