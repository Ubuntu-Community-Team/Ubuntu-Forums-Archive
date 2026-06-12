---
title: "file access time"
date: 2011-01-05
forum: General Help
---

### Post by MichaelBurns on 2011-01-05
Is there a bash command that I can use to determine the last file access time?  I know about -atime option for the find command, but I want to doublecheck to make sure that I'm doing this correctly (the output when I use find -atime isn't what I expect).

---

### Post by noah++ on 2011-01-06
```
ls -lu
```
Also be sure your filesystem wasn't mounted with **noatime** option.

---

### Post by gmargo on 2011-01-06
The **stat(1)** command will print information from the inode such as the access time.

---

### Post by sisco311 on 2011-01-06
Since 8.04, Ubuntu defaults to the relatime mount option: [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

If the partition is mounted with relatime, then access time is only updated if the previous access time was earlier  than  the current modify or change time.

---

### Post by MichaelBurns on 2011-01-06
> **noah++ said:**
> Also be sure your filesystem wasn't mounted with **noatime** option.Hmm.  Now that you mention it, I wonder if I should expect the access time to make sense.  This regards an NTFS normally used by a Windowser.  Ubuntu seems to have quite decent NTFS tools from my naive user viewpoint, but **find -atime** disagrees with **ls -l**.  **ls** *was indeed* the command that gave me unexpected results, but I didn't pass the **-u** option, so that was my fault.  (I wonder when Linux will stop being so damn complicated for me.)

> **gmargo said:**
> The **stat(1)** command will print information from the inode such as the access time.That's brilliant!  Thank you.  (although **apropos** has now failed me miserably for the first time :( )  BTW, how do I use "%x" to extract just the access time from the output?  (It's in the manpage regarding access time, but I don't know how to use it.)

> **sisco311 said:**
> Since 8.04, Ubuntu defaults to the relatime mount option: [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)Thank you for the link of info.  I wonder if that still applies if I'm interested in Windows' access times.  I actually don't want my access to this NTFS to be recorded, and now I'm concerned: what exactly counts as "access"?

---

