---
title: "using readahead"
date: 2011-01-25
forum: General Help
---

### Post by Sleven7 on 2011-01-25
I found this article 

[http://wiki.debian.org/BootProcessSpeedup](http://wiki.debian.org/BootProcessSpeedup)

and tried to follow the instructions on the first mod.
On the second command I get this error:

root@unit1:/home/sleven# touch /etc/readahead/profile-once
touch: cannot touch `/etc/readahead/profile-once': No such file or directory

Used the file browser and noticed that readahead is readahead.d 
and the file profile-once does not exist

Is the information in the article out of date? 
Is there a new procedure for using readahead? 
If so is there an updated article somewhere?

yes I read the man page, but am unsure how to configure files.
I'm also trying the mod in Debian 6.0 not Ubuntu, wanted to try it there before implementing it in Ubuntu

---

