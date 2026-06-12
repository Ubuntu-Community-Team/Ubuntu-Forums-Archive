---
title: "Ubuntu 10.04 crashed"
date: 2011-01-13
forum: General Help
---

### Post by niceguy123 on 2011-01-13
My desktop using Ubuntu 10.4 (I recently ungraded from 9.04) crashed. That is Ubuntu is not loading. At first I get a Ubuntu icon and count % of cheeking system and before it reaches 50% a linux screen comes up with error messages:

Last six lines:

```

mountall: fsck / (9290) terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (9289) terminated with status 3
Mount of filesystem failed.
a maintenance shell will now be started.
CONTROL-D will termainae this shell and re-try.
roo@computername-desktop:"# _

``` 

Any ideas how to revive Ubuntu?

thanks

---

### Post by tredegar on 2011-01-13
Your root filesystem has errors.
**fsck **was unable to repair them:

The exit code returned by fsck is the sum of the following conditions:
4 - **File system errors left uncorrected**

Try booting from a live CD and running **fsck** on your _unmounted_ root partition.

Good luck.

---

### Post by niceguy123 on 2011-01-15
> **tredegar said:**
> Your root filesystem has errors.
**fsck **was unable to repair them:

The exit code returned by fsck is the sum of the following conditions:
4 - **File system errors left uncorrected**

Try booting from a live CD and running **fsck** on your _unmounted_ root partition.

Good luck.

Ran CD live and got Linux screen with some info ending with:

```
ubuntu@ubuntu:"$
```

What now?

---

