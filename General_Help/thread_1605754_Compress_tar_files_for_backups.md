---
title: "Compress tar files for backups"
date: 2010-10-25
forum: General Help
---

### Post by e24ohm on 2010-10-25
Folks,
I just read in my Linux+ resources that it is not a wise idea to compress tar files with gzip if my tape drive supports compression. In addition, the resources mention that using gzip for tar files runs the risk of data lost if an error occurs with the compression.

Has anyone seen this issue? Does anyone compress tar files for major backups/restore policies?

---

### Post by MrRichard on 2010-10-25
I use Deja Dup to backup my files, and it has worked splendid so far. Deja Dup backs everything up into 30MB or so sized difftar.gz files. This method cut the filesize almost in half; from 4.7GB to 2.6GB. I've never seen a compressed file corrupted before in my 5 years fiddling with computers.

That's my two cents :guitar:

---

