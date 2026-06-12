---
title: "hash sum mismatch on index file at update"
date: 2010-04-27
forum: General Help
---

### Post by ami_nakata on 2010-04-27
In updates to Hardy I've attempted over the past week or two I've received warning messages from update manager and the same message when I've tried "sudo apt-get update" as an alternative, via the terminal.  Here's the terminal output message:

> Get:1 [http://www.avenard.org](http://www.avenard.org) hardy/release Packages [54.4kB]
Fetched 1B in 0s (1B/s)           
W: Failed to fetch [http://www.avenard.org/files/ubuntu-repos/dists/hardy/release/binary-i386/Packages.bz2](http://www.avenard.org/files/ubuntu-repos/dists/hardy/release/binary-i386/Packages.bz2)  Hash Sum mismatch
E: Some index files failed to download, they have been ignored, or old ones used instead.I'm able to download the Packages.bz2 file by pasting the avengard url for it directly into a browser window's address bar, but I notice that Nautilus reports the file as 53.2 KB while the error message I receive in terminal (via sudo apt-get update) refers to a size of 54.4 KB.  

Update manager continues to report that my system was last updated 12 days ago, and that worries me.  My internet connection is fine, and all *other* mirrors and downloads seem to be properly accessed, so what's going on with [http://www.avenard.org/files/ubuntu-repos/dists/hardy/release/binary-i386/Packages.bz2](http://www.avenard.org/files/ubuntu-repos/dists/hardy/release/binary-i386/Packages.bz2) ?  Thanks!

---

### Post by dcstar on 2010-04-28
> **ami_nakata said:**
> In updates to Hardy I've attempted over the past week or two I've received warning messages from update manager and the same message when I've tried "sudo apt-get update" as an alternative, via the terminal.  Here's the terminal output message:
........!

What you get/don't get from a third-party repository is between you and that repository.

---

### Post by ami_nakata on 2010-04-28
> What you get/don't get from a third-party repository is between you and that repository.

Yes, I see this is a third-party repository. ( Thanks, David. )  I vaguely recall adding it a year or so ago, trying to fix a video problem: I was off-track on that; it didn't help and accessing the avenard site wasn't and isn't necessary.  I still need to solve the problem, though: the "updates available" icon is always "lit"; update manager generates the error message I cited above; and update manager tells me my system was last updated 12 days ago. 

Can I stop apt-get or update manager from trying to download package updates from this site?  How?

cheers,

Ami

---

### Post by plucky on 2010-04-28
> **ami_nakata said:**
> Yes, I see this is a third-party repository. ( Thanks, David. )  I vaguely recall adding it a year or so ago, trying to fix a video problem: I was off-track on that; it didn't help and accessing the avenard site wasn't and isn't necessary.  I still need to solve the problem, though: the "updates available" icon is always "lit"; update manager generates the error message I cited above; and update manager tells me my system was last updated 12 days ago. 

Can I stop apt-get or update manager from trying to download package updates from this site?  How?

cheers,

Ami

**System > Administration > Software Sources** and un-tick the offending repository under the **Other Software** tag.

Good Luck

---

### Post by ami_nakata on 2010-04-28
Thanks, plucky! That did it. And thanks, again, David.

cheers,

Ami

---

