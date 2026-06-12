---
title: "User Groups and password"
date: 2012-09-30
forum: General Help
---

### Post by Kansasguy on 2012-09-30
Attempting to change the login order of 2 users, I disabled my account (administrator). Then went into the User Accounts and tried to change the user number (1000 for me, 1001 for the new account). Problem is, when I try to "authenticate", it asks me for my password (and to change it), and it won't accept my password.  I don't know if I accidently changed my password, or if it won't accept it because I "disabled" my account. Funny thing is, the account still works. (Why did I disable it?, thought it would cause the other one to boot up first--wrong)

   Averatec (older) laptop, dual booted with XP and Linux Mint LXDE (I know, it's not Ubuntu, but this is a huge forum and they are so much the same)

Thanks in advance

---

### Post by deadflowr on 2012-09-30
Yeah, when you disabled the account it locks out the password.

here's how to reset it:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

I myself haven't ever thought about how to change the login order. That's something I'll have to take a look at. At a glance, it seems to be alphabetical.

---

### Post by Kansasguy on 2012-09-30
Thanks for the quick reply!

And Oops, I meant LXDE, not Xfce, probably doesn't make any difference
Will try what you said and get back to you,  Thanks again

---

### Post by Kansasguy on 2012-09-30
Worked great, thanks so much.  Updating (264 updates) Maybe there will be a login manager in there.   Then going to check into LXDM.  I tried changing the user number from 1000 to 1002 for me, and left the other one at 1001, didn't help.      Thanks again

---

### Post by JKyleOKC on 2012-09-30
Changing your user number may change ownership of files that you created under the original number. The metadata, including file ownership and group, is actually stored by the user number rather than the user name. I don't know if the number-change routines go through the entire hard disk and correct all affected files, but I certainly would not expect them to do so. After all, one purpose of making such a change might be to take ownership away from the original creator (although that could be done more easily by "chown" than by changing a user number).

You can find out by doing "ls -l" in a directory where you stored some files before making the change. If they still show your user name as owner, then they were corrected. If they simply show as owned by "1000" and group "1000" then no correction occurred.

---

