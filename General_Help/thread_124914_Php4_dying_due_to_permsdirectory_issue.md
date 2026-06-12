---
title: "Php4 dying due to perms/directory issue"
date: 2006-02-02
forum: General Help
---

### Post by glave on 2006-02-02
I recently moved my /var over to a new partition and screwed up ownership and perms when I did it. Life has not been fun since....

I'm now getting errors like this from php scripts:
open(/var/lib/php4/sess_147d195cf3897e98777ee85d8ea89a72, O_RDWR) failed: No such file or directory 

I have tried uninstalling php4 and reinstalling, it did not help out though. I tried moving the directory to another name (/var/lib/php4) and then reinstalling php4, also no luck.

What perms does /var/lib/php4 need or how could I possibly fix this?

---

