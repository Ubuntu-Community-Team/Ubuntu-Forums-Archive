---
title: "visudo on karmic"
date: 2010-01-03
forum: General Help
---

### Post by tiagoscd on 2010-01-03
Hi,

I edited the **/etc/sudoers** using the **sudo visudo** command, but the changes doesn't have effect.

```
tiago ALL=NOPASSWD: /sbin/hdparm*, /bin/mount*, /bin/umount*
```

I want to disable password to the user **tiago** execute the commands **hdparm**, **mount** and **umount** without restrictions.

I tried to change the line to the follow but the error persists.

```
tiago ALL=NOPASSWD: /sbin/hdparm, /bin/mount, /bin/umount
```

I restarted the computer, and the changes also doesn't have effect.

---

### Post by jonest1 on 2010-01-03
Can you give the exact output of the error you receive, or does it just ask for a password?

---

### Post by tiagoscd on 2010-01-04
Just asks for the password, without errors.

The visudo is working on Karmic for somenone?

---

### Post by SuperSonic4 on 2010-01-04
What happens if you specify those commands as 3 different lines?

---

### Post by tiagoscd on 2010-01-04
The problem persists.

I got the same problem to autostart firestarter, when Karmic was a alpha release.

---

### Post by bodhi.zazen on 2010-01-05
The problem is one of syntax. If a user has multiple permissions they can conflict and I believe the last rule takes precidence

From [http://linux.die.net/man/5/sudoers](http://linux.die.net/man/5/sudoers)

> When multiple entries match for a user, they are applied in order. Where there are conflicting values, the last match is used (which is not necessarily the most specific match). So, early in /etc/sudoers you are putting your nopasswd rule, and then it is over ruled later probably in the %admin line.

Put your nopasswd option LAST =)

---

### Post by tiagoscd on 2010-01-05
bodhi.zazen,

Thanks, the line was before end of file! I changed it and the problem was solved.

Thanks for all!

Regards,

Tiago Hillebrandt

---

