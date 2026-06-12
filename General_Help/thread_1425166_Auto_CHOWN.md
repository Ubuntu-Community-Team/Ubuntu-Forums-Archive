---
title: "Auto CHOWN"
date: 2010-03-08
forum: General Help
---

### Post by jfreak53 on 2010-03-08
Ok wierd question here.  I want to make a script that reads the current directory location, for example:

/home/user/dir1

Then grabs the second dir in that list:

user

Then chowns -R user:user %1.

Basically I want a script to read the dir then use the second dir name as a user and group name in chown and pass final parameter from what I give it.  I have a lot of things that I constantly chown to the current users dir and this would make things so fast and easy.  Any ideas?

---

### Post by cong06 on 2010-03-09
you want to get the user from a specific folder?

```

ls -al | grep "^d" | head -5 | awk 'END {print $3, $4}'

```
This will print out the 5'th folder entry's user followed by it's group.

If you did something like this:
```

user=`ls -al | grep "^d" | head -5 | awk 'END {print $3}'`
group=`ls -al | grep "^d" | head -5 | awk 'END {print $4}'`
chown -R $user:$group *

```
It would set the user and group for all files based on the 5th one.

over view:
ls: list the contents
grep: grabs entries starting with (hence the "^") d
head -5: lists only the first 5 items passed to it (ie folders)
awk: END means it only preforms at the end (ie: last entry) and prints the 3rd or 4th item to sdout

---

### Post by jfreak53 on 2010-03-09
Perfect!  The only thing I changed was I changed the head from 5 to 1 to get current dirs user and group since that will always be correct for my usage.

Thanks for the help.

---

