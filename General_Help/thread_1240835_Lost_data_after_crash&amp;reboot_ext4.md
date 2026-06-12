---
title: "Lost data after crash&amp;reboot ext4"
date: 2009-08-15
forum: General Help
---

### Post by Blaazen on 2009-08-15
Hello,
my Kubuntu freezed and I rebooted system. But files opened in time of crash have size 0bytes now. It's known bug in ext4, I use kernel xxx.28 and there is probably no patch for it yet.
However, lost file is pascal unit and I have backup two days ago (12-th August), but I believe there are still fresh data on harddisk, because the file is rewritten in every "build" and I compiled it many times that day(it happened on 14-th august evening). There was some work made on it and I don't want to write it again :-). Original size was 45kB and I know that filesystem saves files in blocks and I hope I can recover at least the first block (I don't know blocksize on ext4).
So, does anybody know how to change filesize without rewriting it? Something like "touch" or "dd" command, or some low-level utility?
Thank for any help.
Blaazen

---

