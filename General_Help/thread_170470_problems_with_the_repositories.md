---
title: "problems with the repositories"
date: 2006-05-04
forum: General Help
---

### Post by orlox on 2006-05-04
I use Xubuntu dapper, and lately, when i try to download something from synaptic, it fails too often. I tried to reload the repositories, the download of many of htose files also fails!...Do I need to change the repositories to make it work right?

---

### Post by Sutekh on 2006-05-04
What sort of error do they fail with?  Unresolved host?  GPG key errors?  Are they local repositories?  For example 
```
deb http://**us.**archive.ubuntu.....
```instead of
```
deb http://archive.ubuntu.....
```

---

### Post by orlox on 2006-05-04
...It just worked...don't know how. Have been failing for the last week now, and it suddenly fixed by its own...

---

### Post by Sutekh on 2006-05-04
Are you using local repositories.  I have had this occur before, when I use **au.** repositories.  I either remove the au. or just wait till things work out.                      Repositories can be mysterious things to me sometimes.

---

### Post by orlox on 2006-05-04
They were local repositories, with the cl prefix (from Chile)...But it's working now. However, if it fails again, how can I remove the prefix? I know there is a file that holds the repositories, but I don't know where it is...

---

