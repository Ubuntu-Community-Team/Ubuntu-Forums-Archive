---
title: "Shutdown Cleanup?"
date: 2011-01-28
forum: General Help
---

### Post by Dusenberg on 2011-01-28
Help please?

10.10 on laptop.

I need to do some cleanups of certain folders/files when I shutdown.  I have added entries to /etc/gdm/PostSession/default but it isn't working. 

Here's the file
```

z:~$ cat /etc/gdm/PostSession/default
#!/bin/sh
echo "$( date ) Trying to rm...." >> /home/z/postsess.txt
rm -R /home/z/.thumbnails/normal
rm -f /home/z/.bash_history
exit 0
z:~$

```

I know the file executes because the postsess.txt contains entries.

Anyone got ideas why the files aren't being removed?

Thanks

---

### Post by dino99 on 2011-01-28
why you dont install & use "bleachbit" to do such job ? (look at synaptic)

---

