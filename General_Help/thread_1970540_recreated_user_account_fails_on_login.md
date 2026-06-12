---
title: "recreated user account fails on login"
date: 2012-05-01
forum: General Help
---

### Post by sldavid on 2012-05-01
Hello all.

Have a situation on lubuntu 12.04 64 where a user account was deleted and recreated but will fail on login.

The user account and files associated with the account were deleted. The account was recreated with the same user name and password.

Login attempts visually go through the process but end up back at the display manager.

Additional user accounts (different names) work successfully. 

Any ideas?

Thanks

---

### Post by marinara on 2012-05-02
The ~/.xsession.err (error file) contains a line "cannot find /home/my_user_name/.profile".
(from this thread [http://ubuntuforums.org/showthread.php?t=1340887](http://ubuntuforums.org/showthread.php?t=1340887) )
can you check that log and the system log?

---

### Post by sldavid on 2012-05-02
Thanks for your reply marinara.

The problem has gone away. I recreated the user account a third time to generate the log (~/.xsession.err) and now the account works fine.

I wish I knew what changed - updates from the Update Manager?

Should it happen again I will post the log information here.

Thanks again for your help.

---

