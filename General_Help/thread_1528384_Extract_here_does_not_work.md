---
title: "Extract here does not work"
date: 2010-07-10
forum: General Help
---

### Post by aveminus on 2010-07-10
When i try to extract a tar by doing right click and then etract here it shows me this

tar: gnutella/data.erl: Cannot utime: Operation not permitted
tar: gnutella/test.erl: Cannot utime: Operation not permitted
tar: gnutella/servent.erl: Cannot utime: Operation not permitted
tar: gnutella/hostcache.erl: Cannot utime: Operation not permitted
tar: gnutella/utils.erl: Cannot utime: Operation not permitted
tar: gnutella/lists_random.erl: Cannot utime: Operation not permitted
tar: gnutella/Makefile: Cannot utime: Operation not permitted
tar: gnutella/capitals/Africa.txt: Cannot utime: Operation not permitted
tar: gnutella/capitals/Asia.txt: Cannot utime: Operation not permitted
tar: gnutella/capitals/Scandinavia.txt: Cannot utime: Operation not permitted
tar: gnutella/capitals/South_America.txt: Cannot utime: Operation not permitted
tar: gnutella/capitals: Cannot utime: Operation not permitted
tar: gnutella/capitals: Cannot change mode to rwx------: Operation not permitted
tar: gnutella: Cannot utime: Operation not permitted
tar: gnutella: Cannot change mode to rwx------: Operation not permitted
tar: Exiting with failure status due to previous errors



But then when I use Ark I can view the file and then extract it.
How can I get this right click->extract here  feature working ???

---

### Post by lidex on 2010-07-10
Are you trying to extract to a directory owned by someone else or root?

---

### Post by aveminus on 2010-07-10
No I have read write permissions in that directory. This problem is only there when i use file-roller . When I use some other archiver software like Ark or Xarchiver I do not have this problem.

---

