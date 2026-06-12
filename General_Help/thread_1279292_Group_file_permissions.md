---
title: "Group file permissions"
date: 2009-09-30
forum: General Help
---

### Post by cfrolander on 2009-09-30
I've got my webserver running under the username: www-data. I've created a new group called webusers and added www-data and my account (cody) to said group. I've then chowned all folders in my /www/ folder to www-data:webusers, and chowned all folders (including /www/) to 775.

All files are chown to www-data:webusers, and all files chmod to 664.

My www-data user can still access all the data as needed, but my 'cody' user can't. Is there something I need to do to cause the group permissions to apply?

Here's some console output:
```
cody@runslow:/storage/www/portal/templates/test$ id cody
uid=1000(cody) gid=1000(cody) groups=1000(cody),4(adm),20(dialout),24(cdrom),46(plugdev),108(sambashare),112(lpadmin),113(admin),1004(webusers)
cody@runslow:/storage/www/portal/templates/test$ ls -l
total 4
-rw-rw-r-- 1 www-data webusers 4 2009-09-30 13:06 test.bin
cody@runslow:/storage/www/portal/templates/test$ rm test.bin
rm: remove write-protected regular file `test.bin'? y
rm: cannot remove `test.bin': Permission denied
cody@runslow:/storage/www/portal/templates/test$

```

---

### Post by cfrolander on 2009-09-30
I was able to find the issue. For all people who might be having this problem in the future: You need to lot out and back into your console session! Easy fix.

---

