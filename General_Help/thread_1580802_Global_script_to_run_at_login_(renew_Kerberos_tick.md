---
title: "Global script to run at login (renew Kerberos tickets)"
date: 2010-09-23
forum: General Help
---

### Post by Lucky. on 2010-09-23
This is a spin-off of [this thread](http://ubuntuforums.org/showthread.php?t=1575699).

I would like to run the following command for all users once they login.  The command auto-renews kerberos tickets before they expire.

```
krenew -K 10 -b
```

I know I can do this on a user-by-user basis by adding this to each user's "startup applications".  But is there a more global place to put this?  Perhaps I could add this line to a PAM script or something (I don't quite understand what PAM is, but I think I'm using that with Kerberos.)  Yeah, I'm really lost here.

---

### Post by anirudhtomer on 2010-09-23
put your command into the script file "/etc/profile" because that is the very first script that runs when a login shell is created.

do not put it into script files that run when a non-login shell is created (like .bashrc in your home folder...though they run for login shell as well but only once...leave it) because you want the command to run only when the users login.

I hope it helps.

---

### Post by Lucky. on 2010-09-23
Thanks!  Sheesh, I feel silly.  I've used /etc/profile to set my umask, but it never dawned on me to add stuff to it.  Whooo!

Thanks again, I really appreciate it.

---

### Post by Lucky. on 2010-09-25
Bum deal!  Thought for sure this would work fine, but for some reason it didn't. "ps -A" yielded krenew as a defunct process.  Manually running the command works though, so something must be happening out of order here.

Perhaps something else loads after /etc/profile that makes krenew work.  Hmmm..

Thanks anyway though.  Thought for sure this would be the ticket.

---

### Post by Lucky. on 2010-09-27
Scratch that, working good.  Don't know what the problem was before, but it's been solid for a few days now.

---

