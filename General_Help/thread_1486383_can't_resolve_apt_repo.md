---
title: "can't resolve apt repo"
date: 2010-05-17
forum: General Help
---

### Post by bluethundr on 2010-05-17
I am trying to use some repositories from the launchpad.net site for my hardy server. 

however I can't seem to get any of the repo hosts to resolve. I can bring them up in a browser no problem. But apt doesn't see them... here's one example. 

This is the current contents of my sources.list
```


deb http://mirrors.ccs.neu.edu/ubuntu/ hardy main
deb-src http://mirrors.ccs.neu.edu/ubuntu/ hardy main


```

and this is what happens any time I try to use these repositories...

```

root@cloud5:/etc/apt# aptitude update
Err http://mirrors.ccs.neu.edu hardy Release.gpg
  Could not resolve 'mirrors.ccs.neu.edu'


```

Launchpad _seems_ like an excellent resource! If only I could get it to work!!! :confused:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
Reading package lists... Done

---

### Post by dcstar on 2010-05-18
> **bluethundr said:**
> I am trying to use some repositories from the launchpad.net site for my hardy server. 
........
```

root@cloud5:/etc/apt# aptitude update
Err http://mirrors.ccs.neu.edu hardy Release.gpg
  **Could not resolve 'mirrors.ccs.neu.edu'**


```

Launchpad _seems_ like an excellent resource! If only I could get it to work!!! :confused:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
Reading package lists... Done

mirrors.ccs.neu.edu is some site **your** DNS cannot resolve.

---

