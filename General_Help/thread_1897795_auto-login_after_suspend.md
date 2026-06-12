---
title: "auto-login after suspend"
date: 2011-12-19
forum: General Help
---

### Post by pwnage101 on 2011-12-19
Is there a shell script somewhere in the system files that is executed after pressing the sleep/suspend button? There are some aspects of the current implementation that I would change.

If I could, I would remove:
-the unnecessary fade-to-black effect
-login prompt upon wakeup

I can do so with the command
```
sudo pm-suspend
```
but that means I have to type my password just to suspend!

specs:
Ubuntu 11.10 (fully updated)
Gnome 3 shell

---

### Post by pwnage101 on 2011-12-20
I found out how to disable the lock screen after resume:
[http://ubuntuforums.org/showpost.php?p=9232551&postcount=6](http://ubuntuforums.org/showpost.php?p=9232551&postcount=6)

> In the file /etc/default/acpi-support there is a line
```

LOCK_SCREEN=true

```
which can be commented out to disable screen lock. So just put a '#' in front of it, making it:
```

# LOCK_SCREEN=true

```



works on my Ubuntu 11.10

---

