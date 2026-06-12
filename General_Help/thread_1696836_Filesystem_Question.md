---
title: "Filesystem Question"
date: 2011-02-27
forum: General Help
---

### Post by darkdragn on 2011-02-27
I feel terrible asking such a noob-ish question, however no amount of Google-ing has yielded any answers:
Is there a command to read the contents of an EXT4 filesystem's BadBlocks inode?
Is there a command to see detailed and descriptive information on a filesystem? (Such as what features are enabled, what features are available yet not enabled, descriptive contents of previous fsck logs, inode layout including SuperBlock Backups)

Again, I'm sorry for bothering you guys over such seemingly trivial commands, I just can't find any tools for these uses to save my life, and they would be very helpful. Especially with a Reiserfs, as far as the information tool goes. The other is just a for my own information kind of question.(The EXT4 BadBlocks question, I mean.)

---

### Post by dcstar on 2011-02-28
> **darkdragn said:**
> I feel terrible asking such a noob-ish question, however no amount of Google-ing has yielded any answers:
Is there a command to read the contents of an EXT4 filesystem's BadBlocks inode?
Is there a command to see detailed and descriptive information on a filesystem? (Such as what features are enabled, what features are available yet not enabled, descriptive contents of previous fsck logs, inode layout including SuperBlock Backups)

Again, I'm sorry for bothering you guys over such seemingly trivial commands, I just can't find any tools for these uses to save my life, and they would be very helpful. Especially with a Reiserfs, as far as the information tool goes. The other is just a for my own information kind of question.(The EXT4 BadBlocks question, I mean.)

```
sudo dumpe2fs -b /dev/whatever
```

---

