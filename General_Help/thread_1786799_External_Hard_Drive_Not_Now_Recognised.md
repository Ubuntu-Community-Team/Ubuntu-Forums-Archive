---
title: "External Hard Drive Not Now Recognised"
date: 2011-06-20
forum: General Help
---

### Post by gjohnno on 2011-06-20
Recently I took the internal hard drive from my old desktop PC (Ubuntu 10.04 ) placed it into an external HD Case connected it up to my new desktop PC (Ubuntu 10.04
) and I could access the files on the external HD, that is until this weekend, I now get this error message

**Unable to mount 319 GB Filesystem**

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Could someone please advise me what needs to be done , so I once again view and access the files held on my external HD

Your assistance is very much appreciated

---

### Post by inameiname on 2011-06-20
Sometimes this helps when you get unable to mount issues. But only if the drive in question is formatted in NTFS:

```

For repair of an ntfs drive failing to mount error (often when computer is switched off either in the middle of startup or shutdown):

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda2    # where 'sda2' is mounting point of the ntfs drive

```

If it is NTFS, and that works, all of the file should still be there, and all will be well. Its usually just a bad read of the contents / boot section as to what was corrupted or whatever.

---

