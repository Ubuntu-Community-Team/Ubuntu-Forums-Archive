---
title: "sharing subversion from windows to ubuntu virtualbox"
date: 2010-09-23
forum: General Help
---

### Post by retrodans on 2010-09-23
At work I have the use a windows 7 machine, but can install virtualbox to work on. So in windows I want to checkout an svn repository, share that directory with ubuntu, and manage edit in both.

Most of this works, except for being able to manage the repo in both windows and ubuntu.  If I check the site out in windows and then move to ubuntu to do an 'svn up' I get the response:

```
svn: Can't move '.svn/tmp/entries' to '.svn/entries': Operation not permitted
```

Does anyone have any advice on how to get this to work, or if it's even possible?

---

