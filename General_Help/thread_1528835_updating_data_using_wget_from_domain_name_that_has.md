---
title: "updating data using wget from domain name that has changed."
date: 2010-07-11
forum: General Help
---

### Post by GOwin on 2010-07-11
Hi. I'm wondering what's the best way of updating data I got from a website, that has moved on to a new domain, with some changes in the folder structure.

The old URL for example is [http://folder.old-domain.com](http://folder.old-domain.com) while the new URL is [http://new-domain.com/directory/directory](http://new-domain.com/directory/directory). 

In my hard disk the data are stored in ~/Data_Backup/folder.old-domain.com folder. I used
```
 wget -S -t 0 -c --mirror &#8211;w 2 &#8211;-convert-links http://folder.old-domain.com 
```

So how can I update that folder with contents from the new URL using wget?

I was thinking of using mv to rename the old folder to follow the new URL pattern, but is there a better way of doing this?

---

### Post by GOwin on 2010-07-11
I don't need to follow the directory structure, just need to update contents of the target folder.  Is this correct?

```

wget -S -t 0 -c --mirror –w 2 –-convert-links -N -np -P ~/Data_Backup/folder.old-domain.com http://new-domain.com/directory/directory 

```

---

### Post by GOwin on 2010-07-11
Add the following options:
```
-nH --cut-dirs=2
```

---

