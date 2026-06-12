---
title: "root user!??!?"
date: 2010-05-01
forum: General Help
---

### Post by YongQing on 2010-05-01
ok i've installed Ubuntu many times before. one thing i can never understand is the root user. i was never ever asked to set the password for the root user during installation. and for some reason, maybe i ****ed up during installation of stuff or whatever, i will no longer be able to login to root. it will say my password is incorrect.

WHY CAN'T MY ACCOUNT BE THE HIGHEST ADMIN???

very pissed off right now as this is the 2nd time i'm reinstalling my Ubuntu. (first time was because i might have ****ed the uninstallation of MySQL. now it's wrong root password BS)

---

### Post by kerry_s on 2010-05-01
root is disabled, ubuntu is a sudo system.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by P4man on 2010-05-01
please read this very carefully:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you locked your user account out of the admin group here is how to solve it:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

If you need to reset your password:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by nikhilbhardwaj on 2010-05-01
the root account is disabled by default in ubuntu.
your account is the admin, you can use sudo to perform administrative tasks.

---

### Post by krishnandu.sarkar on 2010-05-01
Thanks for the links guys. I was about to ask the same question.

---

### Post by P4man on 2010-05-01
Since lucid came out, there seems to be a fair number of such posts and questions. Makes me wonder, are you guys upgrading from a previous ubuntu where you unlocked the root account?

---

### Post by polki@mac.com on 2010-05-01
How come this question comes up all the time? I'm just being curious...

---

### Post by P4man on 2010-05-01
My best guess is that it is people upgrading to lucid, that previously unlocked the root account on karmic or whatever because they were not aware off sudo, then googled for a quick fix and found the "wrong" instruction to get them rid of the password dialogue. Upgrading to lucid probably reinstated sudo and locked the root account again (just a guess), so they have a problem now.

---

