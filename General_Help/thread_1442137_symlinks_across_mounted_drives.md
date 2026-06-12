---
title: "symlinks across mounted drives?"
date: 2010-03-29
forum: General Help
---

### Post by zoomiest on 2010-03-29
I couldn't google anything... surely people do this.

What is the syntax if you want to create a symlink to a resource on a mounted drive? am I missing something?

---

### Post by oldfred on 2010-03-29
I create directories - fred & fred/data, edit fstab to mount /usr/local/fred/data automatically, modify permissions and ownership. I rename or delete all my folders in /home.

I was doing this for each folder (13 folders ):
from my home:
ln -s /usr/local/fred/data/Music

But this worked for all 
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

---

### Post by cjhabs on 2010-03-29
> **zoomiest said:**
> I couldn't google anything... surely people do this.

What is the syntax if you want to create a symlink to a resource on a mounted drive? am I missing something?

ln -s /path_of_mounted_drive/more_path link_name

Then "cd link_name" takes you to "/path_of_mounted_drive/more_path"

---

