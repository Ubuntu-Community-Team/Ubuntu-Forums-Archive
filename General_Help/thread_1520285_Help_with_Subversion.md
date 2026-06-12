---
title: "Help with Subversion"
date: 2010-06-29
forum: General Help
---

### Post by Minnesota_Miracle_Man on 2010-06-29
Hey everyone.

I've been tasked with setting up subversion. Everything installed ok, and I seem to be able to import and dump files with little trouble, but I'm just a little confused as to how I'm supposed to configure everything. 

I've seen multiple tutorials on this that seem to have different approaches.

One approach is to create a subversion repository, and create multiple project folders within that central repository folder, i.e.: 

```

cd /home/whatever
svnadmin create svn
svn mkdir file:///home/whatever/svn/project1
svn mkdir file:///home/whatever/svn/project2
```

The other approach, the one I've been using, is to create a normal subversion folder, and create multiple repositories within that folder:

```

cd /home/whatever
mkdir svn
cd ./svn
svnadmin create project1
svnadmin create project2
```

Essentially what I'm asking is, will any complications arise from using one format over the other? Is either one of them better/more common?

---

