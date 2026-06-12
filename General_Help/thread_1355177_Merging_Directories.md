---
title: "Merging Directories"
date: 2009-12-14
forum: General Help
---

### Post by k_squired on 2009-12-14
Let's say I have a duplicate set of directory structures.  However, I want to move the contents (files, i mean) of one into the other.  I have to use sudo, and there are a lot of files, so does anyone know of how to do that in one fell swoop?

Thanks.

---

### Post by ankspo71 on 2009-12-14
Have you tried the move command?

sudo mv <directory path> <destination directory path>
```
sudo mv /home/yourname/mystuff/ /home/yourname/mystuff2/
```Make sure there is a space between the two paths too.
Sudo would be required if working outside your own home directory too.

The copy 'cp' command can do the same, except it won't actually remove the original directory and contents.

---

### Post by bodhi.zazen on 2009-12-14
```
sudo bash -c "yes no | cp -iR /source/* /destination/"
```

source where you are merging from
destination where you are merging to

---

