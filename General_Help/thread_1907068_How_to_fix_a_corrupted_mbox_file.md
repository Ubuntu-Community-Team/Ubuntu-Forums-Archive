---
title: "How to fix a corrupted mbox file?"
date: 2012-01-10
forum: General Help
---

### Post by Marcelo Ruiz on 2012-01-10
Hi All!

I am having problems with Evolution: the mbox file seems to be corrupted. I tried all the methods I could find to solve the problem, but they do not assume the mbox file is corrupted (they do require moving files, deleting the index and folders.db files, and so on).
Since I tried them all, I must assume the mbox file itself is corrupted (also after trying the methods I mentioned above, I saw e-mails dated in 1954 and 2036, so something is really wrong there).
Is there any way to repair a corrupted mbox file? Also, is there any way to eliminate duplicated e-mails from it?
I am using Evolution 2.32.2 in Maverick.
Thanks!

---

### Post by Marcelo Ruiz on 2012-01-10
Well, I finally figured out how to do it: just download and run the following Perl script: [http://wdr1.com/hacks/mbox-dedup.pl]("http://wdr1.com/hacks/mbox-dedup.pl")
It will remove all the duplicate e-mails and will not include those that are corrupted.
Cheers to the developer!

---

