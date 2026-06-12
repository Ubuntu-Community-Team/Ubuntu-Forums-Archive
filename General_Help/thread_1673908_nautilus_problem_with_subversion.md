---
title: "nautilus problem with subversion"
date: 2011-01-23
forum: General Help
---

### Post by hawthornso23 on 2011-01-23
New subversion user here.

I've run into a nasty problem. It seems that nautilus chokes any time it tries to display a directory containing .svn files. There seems to be some sort of timeout involved per object under version control. The larger the directory, the longer it takes to display. I'm talking minutes here for a fairly ordinary sized directory.

Now I know that nautilus is painfully slow even at the best of times, but this is just ridiculous. These delays are crippling.

I have no problem with nautilus and svn files on my work machine, which has centos. So it looks to me like something is misconfigured somewhere. And it is something specific to .svn files.

Has anyone got any suggestions?

---

### Post by hawthornso23 on 2011-01-23
Problem now solved. I installed the package nautilus-script-collection-svn and all is now fine.

---

