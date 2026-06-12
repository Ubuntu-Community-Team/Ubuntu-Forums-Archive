---
title: "Mount Points and Dir Structure"
date: 2009-12-12
forum: General Help
---

### Post by ask21900 on 2009-12-12
I am somewhat new to Ubuntu, and Linux in general and would like, once again, to get the advice of the experts in the community.  First, let me say "Thank you"  this forum has been in invaluable resource, and the people who frequent this are true lifesavers.

On to my question(s)...

What effect do mount points have on the system (in regards to overhead, access time, etc.)?

My situation is this:  I have a file server which was just ported to Ubuntu from Windows.  Having not planned the directory structure very well when I originally created the system several years ago, I now find myself concerned that I will run out of space shortly.

I have 6 main "roots" to my data (referring to storage data only, not the filesystem root).  I have roughly 17TB of data, and several programs and other scripts that use and manipulate the data, so moving data around (such as changing the dir structure) is not really an option.  I do, however, need to essentially create an unlimited potential filesystem with what is already in place.

My thought is to basically create many mount points to achieve what I need.  I would however have the potential of hundreds (maybe even thousands, several years in the future) of mount points.  Will this create an adverse effect?  Is there a more suitable solution to fit my needs?

Thank you all for all your help!!

---

### Post by dcstar on 2009-12-12
> **ask21900 said:**
> 
..........
My thought is to basically create many mount points to achieve what I need.  I would however have the potential of hundreds (maybe even thousands, several years in the future) of mount points.  Will this create an adverse effect?  Is there a more suitable solution to fit my needs?


Mount points mount filesystems, unless you have "hundreds" of filesystems then you just cannot invent them out of thin air to use them:

```
man mount
```

---

### Post by ask21900 on 2009-12-13
Is there a better way of doing this?  I thought of symlinks, and played with them a little to get a better idea of their behavior, but I am thinking that with the constant adding and renaming of data, I would probably find myself continuously getting a "File not found" error.

---

