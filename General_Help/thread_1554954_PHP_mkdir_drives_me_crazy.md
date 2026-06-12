---
title: "PHP mkdir drives me crazy"
date: 2010-08-17
forum: General Help
---

### Post by jim001 on 2010-08-17
Hello

My PHP script is calling mkdir(name, 0777) from apache2 php module on a SSHFS mounted folder . I am getting "permission denied" error even though I set chmod 777 to target folder. I tried different users for SSHFS including www-data, but no success at all.

If I run the same script through PHP CLI for SSHFS mounted folder, it works fine as expected for all different SSHFS users.


How do I get more detailed error log for php module running under apache?
Can someone help me troubleshoot or resolve this please?

Thanks

---

