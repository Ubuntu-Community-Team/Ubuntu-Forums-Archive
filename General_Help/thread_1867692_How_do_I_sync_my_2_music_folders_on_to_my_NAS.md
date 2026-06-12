---
title: "How do I sync my 2 music folders on to my NAS?"
date: 2011-10-23
forum: General Help
---

### Post by xaegis on 2011-10-23
Hello,
I cannot figure out how to sync my music folders from 2 different computers to my NAS to be streamed  back via my DAAP server.

How would I do this? I already have the DAAP up and streaming my content, but how would I mirror my music folders onto the NAS so that all music is universal? Or am I looking at this wrong?

Thanks in advance.

Using Ubuntu 11.10 on all machines. and a Netgear Readynas Duo running Debian I think.

---

### Post by hwttdz on 2011-10-23
I think the "good" answer is rsync.  I'd probably do something like a find with a date or a cp -u in a cronjob.

---

### Post by rahilm on 2011-10-23
just learned this piece of awesomeness today! try rsync!
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by xaegis on 2011-10-23
Perfect, Thanks everyone!  :)

---

