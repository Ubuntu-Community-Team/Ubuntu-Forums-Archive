---
title: "Working with rsync"
date: 2009-10-13
forum: General Help
---

### Post by David Vincent-Jones on 2009-10-13
I have been using rsync for some time to quickly update my backup image collection. In general it works well. I am using the '-av' options (I only use the 'v' so that I do at least know that something is working).

The problem is that if I delete any files on my computer drive the backup is not updated with the deletions and I do not see an option that allows me to totally mirror the computer files onto the back-up.

Help would be appreciated.

David

---

### Post by CharlesA on 2009-10-13
Add the --delete switch.

---

### Post by zer0x on 2009-10-13
Hi,

If I understand correctly, I think you just need to add the --delete option.

HTH

zer0x

---

### Post by andrew.46 on 2009-10-14
I might suggest a small word of caution before adding delete options to the reasonably complex world of the rsync commandline which is to initially use the:

```
--dry-run
```

option to make sure that the right files are being deleted :).

Andrew

---

