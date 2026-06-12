---
title: "rsync backup maintaining path from root"
date: 2011-05-21
forum: General Help
---

### Post by alienspaces on 2011-05-21
I want to preserve the full path to my directory that I plan to backup. 

If I want to backup the following directory recursively

/user/ray/svn

to 

/volume/mirror 

So that I end up with 

/volume/mirror/user/ray/svn

what rsync command options should I use? The typical -a option doesn't preserve the "/user/ray/svn" path.

---

### Post by SecretCode on 2011-05-21
```
rsync /user/ray/svn/ /volume/mirror/user/ray/svn/ -ar
```

If you are looking for a way to specify "user/ray/svn" only once, you'll have to use a shell variable or look into the --include and --exclude options.

---

### Post by alienspaces on 2011-05-22
Thanks for your help. I used shell variables as you suggested to solve it.

---

