---
title: "List of installed packages by repository through commandline?"
date: 2011-02-11
forum: General Help
---

### Post by riverfr0zen on 2011-02-11
I know dpgk --get-selections will list all installed packages, but is there a way to also get the repository each belongs to as well? 

I need to do this through the command line.

---

### Post by DanneStrat on 2011-02-11
Hi!

You can try this:

```
aptitude search ~i -F "%s# %p"
```

I think you need to have aptitude installed

but you can try the command anyway.

Good luck.

---

### Post by riverfr0zen on 2011-02-11
Awesome, thanks! I think that got me started at least to search w/ aptitude and its various options. 

The ones here are particularly interesting:
[http://superuser.com/questions/132346/find-packages-installed-from-a-certain-repository-with-aptitude/200505#200505](http://superuser.com/questions/132346/find-packages-installed-from-a-certain-repository-with-aptitude/200505#200505)

---

### Post by DanneStrat on 2011-02-11
> **riverfr0zen said:**
> Awesome, thanks! I think that got me started at least to search w/ aptitude and its various options. 

The ones here are particularly interesting:
[http://superuser.com/questions/132346/find-packages-installed-from-a-certain-repository-with-aptitude/200505#200505](http://superuser.com/questions/132346/find-packages-installed-from-a-certain-repository-with-aptitude/200505#200505)

You will be able to get more detailed info about your installed

packages with aptitude. That article looked promising by the way!:)

---

