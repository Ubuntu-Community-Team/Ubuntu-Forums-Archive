---
title: "How to change default group for new files in directory"
date: 2009-11-23
forum: General Help
---

### Post by maxxjr on 2009-11-23
I have a 'users' group and a 'developers' group.

I have some users where their default group is 'users', and are also members of 'developers'.

I have a few shared directories for 'developers'.  When a 'developers' user creates a file in one of the 'developers' directories, the group for the file is 'users'.  I would like to change things so that if a 'developers' user creates a file in one of these 'developers' directories, the file will automatically have 'developers' as the group ownership.  If the user creates a file anywhere else, it will have the default 'users' group ownership.

Can someone provide pointers on how to do this?

(I tried Google, but ended up with a bunch of links on how to use chgrp that don't address the particular question I have in this case)

Thanks!

---

### Post by Sam on 2009-11-23
What you're looking for are the setuid/setgid attributes.
```
sudo chgrp developers directory/
sudo chmod g+s directory/
```

This way any new file/directory will belong to the developers group.

---

### Post by maxxjr on 2009-11-23
> **Sam said:**
> What you're looking for are the setuid/setgid attributes.
```
sudo chgrp developers directory/
sudo chmod g+s directory/
```

This way any new file/directory will belong to the developers group.

That did it!  Thanks!

---

### Post by Sam on 2009-11-23
You're welcome ;)

---

