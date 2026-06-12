---
title: "unable to use grep on apache log files"
date: 2010-09-10
forum: General Help
---

### Post by yawnmoth on 2010-09-10
I do "grep filename.php /logs/httpd/www_access_log" and it returns instantly.  I open up www_access_log, however, and do a search for "filename.php" and I find it.  So why isn't grep returning anything?  The file is 100mb big if that makes a difference.

---

### Post by ubulal on 2010-09-10
> **yawnmoth said:**
> I do "grep filename.php /logs/httpd/www_access_log" and it returns instantly.  I open up www_access_log, however, and do a search for "filename.php" and I find it.

You triple checked that path name?  And that you're actually opening that same file in an editor?  And grep is case sensitive, add -i to ignore case.  "which grep" shows the actual grep binary, not some alias or symlink?  Does grep work on other files?

> 
So why isn't grep returning anything?  The file is 100mb big if that makes a difference.

It should not.

---

