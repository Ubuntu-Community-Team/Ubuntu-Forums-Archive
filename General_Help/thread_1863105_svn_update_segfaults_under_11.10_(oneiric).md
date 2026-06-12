---
title: "svn update segfaults under 11.10 (oneiric)"
date: 2011-10-17
forum: General Help
---

### Post by dccarson on 2011-10-17
I just upgraded to 11.10 (oneiric) and now my subversion segfaults every time I do an update.  It also segfaults when I do a checkout.

Note that the segfault occurs at the very end of the command, and does not **seem** to affect the outcome.  However, I am nervous about ignoring it, as I use svn for production code versioning.

Here is the tail end of "strace svn update" on a freshly checked-out working copy (where the checkout also segfaulted).  Note that I get the same results when run on an older working copy that was checked out before I upgraded to 11.10.

```

rename(".svn/tmp/entries", ".svn/entries") = 0
lstat(".svn/entries", {st_mode=S_IFREG|0644, st_size=3001, ...}) = 0
chmod(".svn/entries", 0444)             = 0
write(3, "( success ( ) ) ", 16)        = 16
read(3, "( success ( ) ) ", 4096)       = 16
unlink("towhee/pd-subset/.svn/lock")    = 0
unlink("towhee/branch-release-map/.svn/lock") = 0
:
: <<-- snip -->>
:
unlink("ibis/branch-release-map/.svn/lock") = 0
unlink("ibis/.svn/lock")                = 0
unlink(".svn/lock")                     = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93fe78a000
write(1, "At revision 2337.\n", 18At revision 2337.
)     = 18
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Segmentation fault

```

You can see from the strace that the "At revision 2337.\n" is printed to the terminal, which ought to indicate that svn is done.  Apparently, some kind of cleanup is causing the problem.

Have others seen this problem?  I have seen no other strange behavior with 11.10 so far.

Thanks,
David

---

### Post by dccarson on 2011-10-19
> **dccarson said:**
> I just upgraded to 11.10 (oneiric) and now my subversion segfaults every time I do an update.  It also segfaults when I do a checkout.


After upgrading another computer to 11.10, I'm puzzled by the fact that "svn update" does not cause a sigsegv on the second computer.

What can I try to fix my first computer?  I already tried removing subversion and reinstalling it.  That didn't work.

~David

---

