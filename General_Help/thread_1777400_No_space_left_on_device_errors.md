---
title: "No space left on device errors"
date: 2011-06-07
forum: General Help
---

### Post by gene02 on 2011-06-07
I recently upgraded from Lucid to Maverick, which went fairly smooth.  Then I upped my RAM with some new memory sticks (4Gb to 8Gb).  Since about then, I'm seeing these errors in syslog:

```
Jun  6 22:23:52 howler console-kit-daemon[1224]: WARNING: Failed to add monitor on '/dev/tty2': No space left on device
Jun  6 22:23:59 howler console-kit-daemon[1224]: WARNING: Failed to add monitor on '/dev/pts/0': No space left on device

```

I also get errors when running "tail -f" as root:
```
tail: cannot watch `/var/log/syslog': No space left on device
```

I searched around and I found some other reports of the tail -f error, with the suggestion of increasing fs.inotify.max_user_watches.  I set it to 16384, and that at first resolved the tail -f problem, but now I'm getting that error again even after upping max_user_watches.

I know swap is suggested to be approx. the same size as RAM, but with this upgrade RAM is now bigger than the 5.7G of swap.  Could that be the problem?

Thanks!



[SOLUTION: remove "cgroup_disable=memory" from grub boot command]

---

### Post by oldos2er on 2011-06-07
'No space left on device' refers to hard disk space, not RAM. Can you run **df -h** in a terminal, and post the output here?

---

### Post by gene02 on 2011-06-08
> **oldos2er said:**
> 'No space left on device' refers to hard disk space, not RAM. Can you run **df -h** in a terminal, and post the output here?

You would think so, but there was plenty of space left on the drives and the errors were ocming up in relation to /dev.  I just figured out the problem, though.  It was the "cgroup_disable=memory" line in grub.  I guess that hadn't caused a problem with the previous RAM configuration but did after I upgraded.

Gene

---

### Post by winzter143 on 2011-06-28
> **gene02 said:**
> You would think so, but there was plenty of space left on the drives and the errors were ocming up in relation to /dev.  I just figured out the problem, though.  It was the "cgroup_disable=memory" line in grub.  I guess that hadn't caused a problem with the previous RAM configuration but did after I upgraded.

Gene

I do same error. I also sure the my disk have lot of space. I also run** top** linux command to sure that is my RAM issue.

I also open my grub.conf but i cant see **cgroup_disable=memory** there.

@gene02, can you clarify where is found? Thanks in advance.

---

### Post by richardedwards on 2011-08-20
can someone post the full solution here please?

"How to remove "cgroup_disable=memory" from grub boot command"

thank you

richard

---

