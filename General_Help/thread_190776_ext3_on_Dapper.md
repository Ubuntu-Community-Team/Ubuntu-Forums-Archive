---
title: "ext3 on Dapper"
date: 2006-06-06
forum: General Help
---

### Post by Gannin on 2006-06-06
I noticed with ext3 on Ubuntu, at least on Breezy, it forces a file system check on every 30th booth.  This isn't something I had seen with other distributions.  I was wondering, does the same hold true for Dapper?

---

### Post by mscman on 2006-06-06
Yup :)

---

### Post by Ramses de Norre on 2006-06-06
You can turn that off in fstab if you like.

---

### Post by msak007 on 2006-06-06
Yes it still does. I don't think Ubuntu is the only one that does that though. I used SuSE for a little while to try it out between Breezy and Dapper, and every now and then after a reboot it forced a check. I have a question though...is there some sort of flag on the ext3 drives regardless of the OS? I swear after only rebooting once or twice after installing Dapper, it forced a check on my other 2 ext3 hard drives (used for shares).

---

### Post by ifokkema on 2006-06-06
[QUOTE=Gannin]I noticed with ext3 on Ubuntu, at least on Breezy, it forces a file system check on every 30th booth.  This isn't something I had seen with other distributions.  I was wondering, does the same hold true for Dapper?[/QUOTE]

If it really bothers you, you can change this setting using tune2fs. But you might just as well leave it - it's there to make sure your drives are clean.

---

### Post by ifokkema on 2006-06-06
[QUOTE=msak007]I have a question though...is there some sort of flag on the ext3 drives regardless of the OS?[/QUOTE]

Yes, and you can check your current mount 'count' (and lots of other info) using dumpe2fs.

---

### Post by Gannin on 2006-06-06
The reason I asked is because I've been thinking about switching to xfs when I install Dapper, but I wanted to learn about some of the different variables before making my final decision.  Thanks for the answers :).

---

