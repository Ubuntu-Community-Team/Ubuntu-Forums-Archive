---
title: "Create files with owner:group"
date: 2011-08-16
forum: General Help
---

### Post by wannabegeek on 2011-08-16
Hi all,

I can't figure out how to make files have a different default owner:group..

Example:

I need the users of my group called gpib, to create new files with: username:gpib, 
instead of the default:  username:username


thanks !
wbg

UPDATE:
Perhaps this is the answer...sorry....I had a hard time with the google search string.
[http://ubuntuforums.org/archive/index.php/t-1683938.html](http://ubuntuforums.org/archive/index.php/t-1683938.html)

---

### Post by Toz on 2011-08-16
Yes, the answer is there.

First change the group ownership for the directory:
```
chgrp gpib <directory>
```
Then set the group (setgid) bit:
```
chmod +s <directory>
```

And test:
```
touch <directory>/test
ll <directory>/test
```

---

### Post by The Cog on 2011-08-16
If your users use the command **newgrp gpib** this will change their primary group, and then any files they create will belong to gpib.

---

### Post by wannabegeek on 2011-08-16
thanks  to TOZ andThe Cog.

I followed the instructions in the link on my OP. 

But will also try their suggestions.

---

