---
title: "How can I have multiple users sharing the same Music/Pictures/Video?"
date: 2010-03-07
forum: General Help
---

### Post by clark14 on 2010-03-07
We have a collection of music for the entire family.  Can each user's Music folder point (for lack of a better word) to the same physical directory?  Can I do this with mounts, or is there a better way?

---

### Post by egalvan on 2010-03-07
if it's all Linux, then symbolic links would be the way to go.

And yes, multiple users can use the files at the same time...
Linux was designed this way from the ground up 
(It's The Unix Way)

---

### Post by Neezer on 2010-03-07
> **clark14 said:**
> We have a collection of music for the entire family.  Can each user's Music folder point (for lack of a better word) to the same physical directory?  Can I do this with mounts, or is there a better way?


You could make a separate partition for your media files...give each user permission to read and write the directory, and mount the partition somewhere....that would be my suggestion.

---

### Post by egalvan on 2010-03-07
OK, neezer's post jogged my brain cells a bit...


Are you talking about


several users,
each logging in **one at a time**,
on **one computer**

several users,
each logging in, one or more, **at the same time**,
on **multiple computers**



the first scenario is best served by symbolic links.

The second scenario can be served by symbolic links,
or
sharing via NFS (if all Linux)
sharing via Samba (if Windows is in the mix)


Give us some more information.

---

### Post by clark14 on 2010-03-08
It's all linux and it's one at a time on one computer, so symbolic links it is.  Works like a charm, just what I wanted.

Thanks for the lesson.

Much love to the community.

---

