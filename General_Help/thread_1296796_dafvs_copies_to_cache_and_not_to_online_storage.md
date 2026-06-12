---
title: "dafvs copies to cache and not to online storage"
date: 2009-10-21
forum: General Help
---

### Post by edwinl on 2009-10-21
I run a Kubuntu box with two directories that I want to rsync or copy overnight to my online storage account with Humyo. Humyo allows web dav so I have setup a script that should copy the files that have changed. 

What actually happens is that the rsync command (and I have checked that this also happens if I manually use the "cp" command) moves the files to the cache area under /var/cache/davfs2 and leaves them there. It then creates the files on the Humyo account with zero size. It never actually copies the files from the cache to the oneline storage. 

I have changed the setting in /etc/davfs2/davfs2.conf from use_expect100 1 to use_expect100 0 as suggested and the mounting of the drive seems to be working fine too. 

Can anyone help me please?

---

### Post by estear on 2009-11-09
I have the same problem and i don't know what to do.

---

