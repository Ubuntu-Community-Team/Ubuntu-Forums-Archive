---
title: "/etc/init.d/oracle-xe is missing?"
date: 2011-07-24
forum: General Help
---

### Post by boy18nj on 2011-07-24
I installed oracle xe second time on ubuntu, this time it did not created following script

/etc/init.d/oracle-xe

Please let me know what I am missing?

---

### Post by Waappu on 2011-07-31
Hi,

You can try install again.
First remove your previous install.
[http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#BABFFJIB](http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#BABFFJIB)

And make sure you also remove file
/etc/default/oracle-xe

When you start install see that your system meet Swap Space Requirement
[http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#BABCCEGF](http://download.oracle.com/docs/cd/B25329_01/doc/install.102/b25144/toc.htm#BABCCEGF)

Then you can use e.g. this guide
[https://help.ubuntu.com/community/Oracle](https://help.ubuntu.com/community/Oracle)

This might also interest you
[http://dbswh.webhop.net/dbswh/f?p=BLOG:READ:0::::ARTICLE:2000](http://dbswh.webhop.net/dbswh/f?p=BLOG:READ:0::::ARTICLE:2000)

---

### Post by RichKatz on 2011-08-12
> **boy18nj said:**
> I installed oracle xe second time on ubuntu, this time it did not created following script

/etc/init.d/oracle-xe

Please let me know what I am missing?
============================
What I noticed is that first, it was renamed to oracle-xe-dpkg-new

There are a multitude of issues, however and it looks like Ubuntu 11.04 is missing the /etc/sysconfig directory(which is required by the oracle-xe script!!).    I followed these instructions:

[http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/](http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/)

These instructions had worked just fine on Ubuntu 9, but I was required to upgrade. 

So, Questions:
 
Either some other package needs to create the /etc/sysconfig before installing Oracle XE, and files in that directory?  Or they are moved elsewhere during install? *Most* of Oracle's main files do exist.  But some don't.  I tried to run the tnslistener by itself and it complained that ORACLE_HOME didn't exist (wrong... it did).

Or do we have to manually locate them, create /etc/sysconfig, and move them back? Or modify the oracle-xe script.

Was /etc/sysconfig eliminated or moved?  I see just  a few posts around the net that say "/etc/sysconfig doesn't exist."

If anyone reads this and has any insight, thanks!

-- Rich

---

