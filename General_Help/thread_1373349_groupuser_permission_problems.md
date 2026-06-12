---
title: "group/user permission problems"
date: 2010-01-05
forum: General Help
---

### Post by manolo_asdf on 2010-01-05
i am having a problem with setting up proper user-rights. following problem: (the user aldana cannot write file to folder, though permissions look ok to me):

```

aldana@v37013:/var/www/convoi$ groups aldana
www-data users
aldana@v37013:/var/www/convoi$ ls -la
total 48
drwxrwsr-x 10 www-data root 4096 Dec 28 22:37 .
drwxr-xr-x 10 root     root 4096 Jan  5 21:53 ..
drwxrwxr-x  2 www-data root 4096 Dec 28 22:37 content
drwxrwxr-x  2 www-data root 4096 Dec 28 22:37 css
drwxrwxr-x  6 www-data root 4096 Dec 28 22:37 flvplayer
drwxrwxr-x  3 www-data root 4096 Dec 28 22:37 images
-rw-rwxr--  1 www-data root 1547 Dec 28 22:37 index.php
drwxrwxr-x  2 www-data root 4096 Dec 28 22:37 js
-rw-rwxr--  1 www-data root  110 Dec 28 22:37 robots.txt
drwxrwxr-x  4 www-data root 4096 Dec 28 22:37 smarty
drwxrwxr-x  6 www-data root 4096 Dec 28 22:37 smartyApp
drwxrwxr-x  2 www-data root 4096 Dec 28 22:37 videos
aldana@v37013:/var/www/convoi$ touch b
touch: cannot touch `b': Permission denied

```

why is that? he is group-member of 'www-data'. still he cannot write to it though the www-data is having setting rwx on the directory.

thanks.

---

### Post by manolo_asdf on 2010-01-05
maybe the reason is, that '..' directory is not writable? i thought that it would be enough to have execution rights for directories to be able to create files in child directory?

a real miracle...

---

### Post by bodhi.zazen on 2010-01-05
See if this link helps :

[http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297](http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297)

---

### Post by KeLa on 2010-01-05
Problem is that you have user www-data that have read+write+execute rights and then you have group root to have r+w+x rights.
You need to change rights so that group www-data have r+w+x rights.
sample ls -la looks like this
```
drwxrwsr-x 10 www-data www-data 4096 Dec 28 22:37 .
drwxrwxr-x  2 www-data www-data 4096 Dec 28 22:37 content
drwxrwxr-x  2 www-data www-data 4096 Dec 28 22:37 css
drwxrwxr-x  6 www-data www-data 4096 Dec 28 22:37 flvplayer
...
```

---

### Post by manolo_asdf on 2010-01-05
oh damn... i mixed up the columns (user with group). one of these days were the eyes just wouldn't see it.

many thanks.

---

