---
title: "Backup Script Request"
date: 2010-01-13
forum: General Help
---

### Post by Puzzled Guy on 2010-01-13
Hi

Could someone please write a bash script that will execute these commands one-by-one?

rsync -av /home/hope/Desktop /media/HOPE
rsync -av /home/hope/Music /media/HOPE
rsync -av /home/hope/Pictures /media/HOPE
rsync -av /home/hope/Videos /media/HOPE

Thanks

---

### Post by audiomick on 2010-01-13
Hallo.
Maybe someone will come back with a precise answer.
If not, go and have a bit of a read
[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)
[https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html)

there is a link on the second page to here
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Cheesemill on 2010-01-13
```
#!/bin/bash
rsync -av /home/hope/Desktop /media/HOPE
rsync -av /home/hope/Music /media/HOPE
rsync -av /home/hope/Pictures /media/HOPE
rsync -av /home/hope/Videos /media/HOPE
```

---

### Post by Puzzled Guy on 2010-01-13
Wow! That was quick.

Thanks Cheesemill! The script works.

And thanks for the links, audiomick. I think I'll try to learn how to bash script.

---

