---
title: "cryptroot error with full disk encryption"
date: 2012-07-29
forum: General Help
---

### Post by pbraub on 2012-07-29
Hi Forum,

```
3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

 my system halts after the grub selection with a "_". When cancelled by "esc" the system prompts for the lvm password alongside with an error message.

I run a full disk encryption with only a unencrypted boot partition.

 with the 3.2.0-23 kernel version the error was simply
 ```
/scripts/local-top/cryptroot: line 24: dirname: not found
```

there was a askubuntu question related to a similar problem ([http://askubuntu.com/questions/162000/cryptroot-error-during-boot](http://askubuntu.com/questions/162000/cryptroot-error-during-boot)) but none of the solutions worked for me. I peeked inside the initrd.img and found no dirname binary, but unfortunately I failed in compiling a custom one.

 with the latest upgrade to 3.2.0-27-generic the error message changed to
```
/scripts/local-top/cryptroot: line 24: dirname: not found
/init: eval: line 1: array_cryptroot.backup=bin conf dev etc init lib lib64 proc rootrun sbin scripts sys tmp usr var: not found
/init: eval: line 1: syntax error: bad substitution
/init: eval: line 1: array_cryptroot.backup=: not found
/init: eval: line 1: syntax error: bad substitution

Unlocking the disk [...]:
Enter passphrase:
```

any suggestions how to tackle this issue?
I've been running a 10.10 with full disk encryption for years without any problems.

thank you,
cheers!
peter

---

