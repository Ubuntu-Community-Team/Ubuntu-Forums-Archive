---
title: "Apache2 unable to write to cache folder"
date: 2011-04-06
forum: General Help
---

### Post by researchtj on 2011-04-06
We're trying to have our Wikipedia clone website cache files to a local directory, but the write requests to the directory are being denied according to the Apache2 error log:

PHP Warning: wfMkdirParents: failed to mkdir "/var/www/wikipedia/cache/8" mode 511 in /var/www/wikipedia/includes/GlobalFunctions.php on line 2179

The cache folder has full read/write/execute permissions for all users and is located in the website's directory, so it shouldn't be a permissions issue.

Our server is running Ubuntu 10.10 64bit Desktop Edition. In addition, we are using PHP v. 5.3.3 and Apache v. 2.2.16.

---

