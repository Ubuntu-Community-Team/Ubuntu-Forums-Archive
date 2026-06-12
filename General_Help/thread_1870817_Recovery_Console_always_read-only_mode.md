---
title: "Recovery Console always read-only mode"
date: 2011-10-27
forum: General Help
---

### Post by Dark Slipstream on 2011-10-27
I'm currently running Ubuntu 11.10.

I recently needed to use the recovery console to run some commands, but for some reason my recovery console is in read-only mode.

How can I remove read-only / make it writable?

---

### Post by Dark Slipstream on 2011-10-28
bump, still trying to fix this.

---

### Post by HumbleNoob on 2011-10-31
You may re-mount "/" read-write by typing the code below in recovery mode:

```

# mount -o rw,remount /

```You may want to read the man pages for further information ([http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount))

---

### Post by infinitybot on 2011-10-31
You can always press Ctrl + Alt + F1 , login  using your credentials and execute the commands you need to

---

### Post by Dark Slipstream on 2011-11-01
> **HumbleNoob said:**
> You may re-mount "/" read-write by typing the code below in recovery mode:
 
```

# mount -o rw,remount /

```You may want to read the man pages for further information ([http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount))
 
Thanks, this worked.
 
 
> **infinitybot said:**
> You can always press Ctrl + Alt + F1 , login using your credentials and execute the commands you need to
 
The commands I need to execute have to run before ubuntu boots, so this would not work, in my case.

---

