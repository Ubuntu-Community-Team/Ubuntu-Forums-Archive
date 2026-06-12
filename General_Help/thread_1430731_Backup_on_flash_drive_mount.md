---
title: "Backup on flash drive mount"
date: 2010-03-15
forum: General Help
---

### Post by Trebawa on 2010-03-15
I'd like to make regular backups of my flash drives, but I don't plug them in regularly.  Because of this, I can't just use a scheduled backup application to back them up.  Does anyone know of an incremental backup application that will automatically run backups on media as soon as it's mounted?

---

### Post by ajgreeny on 2010-03-15
If you want to back them up to your hard drive, give each flash drive a volume label to differentiate each one, and I imagine it would be easy enough to write a script to automatically use rsync as soon as the folder named from that volume label appears in /media.

I regret, however, that I am not clever enough to know what that script would be.

---

