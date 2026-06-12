---
title: "w &amp; who show wrong results"
date: 2012-04-16
forum: General Help
---

### Post by heartsbane on 2012-04-16
I have this strange problem that w & who are not showing anybody. who returns no results what so ever and w returns:

```
[~]$ w    
 10:37:28 up 59 min,  0 users,  load average: 1.68, 1.77, 1.69
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT

```

I have tried
```
sudo -s
cat /dev/null > /var/run/utmp
reboot
```

I also tried this:

[http://askubuntu.com/questions/57132/w-showing-wrong-number-of-users-logged-in](http://askubuntu.com/questions/57132/w-showing-wrong-number-of-users-logged-in)
 
Same results

---

### Post by Toz on 2012-04-16
Its a known bug. See: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297"). Feel free to add yourself to the list of affected users.

---

### Post by heartsbane on 2012-04-16
thanks

---

