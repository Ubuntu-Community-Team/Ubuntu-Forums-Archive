---
title: "How to move a directory to another and overwrite the content that matches?"
date: 2011-12-28
forum: General Help
---

### Post by houmank on 2011-12-28
Hello,

I have a folder called functions and would like to move it to my wordpress folder, which also contain a folder with the same name.

I would like to make sure to overwrite all files and subfolders.


I tried this:

```
sudo mv functions/ /var/www/mysite/wp-content/themes/optimize/

```
But it says:

```
mv: cannot move `functions/' to `/var/www/mysite/wp-content/themes/optimize/functions': Directory not empty

```

Any idea?
Many Thanks,

---

### Post by houmank on 2011-12-28
It seem sin Linux there is a different command to achieve this simple task:


```
sudo rsync -azvv functions/ /var/www/mysite/wp-content/themes/optimize/functions/

```

It seems to be working. You guys agree on this or could I have missed out a file?

---

### Post by lswb on 2011-12-28
rsync is a great command especially for syncing and copying large numbers of files and for copying between different systems too. You could also use a simple "cp -r /sourcepath/functions/* /destinationpath/functions" in this case.

---

