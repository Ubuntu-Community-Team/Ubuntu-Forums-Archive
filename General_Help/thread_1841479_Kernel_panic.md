---
title: "Kernel panic"
date: 2011-09-09
forum: General Help
---

### Post by thunderbirdje on 2011-09-09
Hello everyone,

After an automatic update/grade by Ubuntu my computer does not boot anymore in the new kernel 2.6.38.11-generic. 

The error is 
```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

However I can still bit into the older kernel 2.6.38.-10-generic.

If have already Googled this error and compared the .11-generic section to the .10-generic section which looks identical.

I have also tried this according to [this thread]("http://ubuntuforums.org/showthread.php?t=997133"). The terminal responds with 'dpkg: error: unknown option --reconfigure'

```
sudo dpkg --reconfigure linux-ubuntu-modules-2.6.24-22-generic
```

Can I somehow fix this problem? Can I let .11 reinstall?

I am happy to provide the necessary details or snapshot from the error, grub, etc...

---

### Post by TeoBigusGeekus on 2011-09-09
The specific version of linux modules (2.6.24-22) apply to the time the aforementioned thread was written - namely 2008.
Find the version of your linux modules
```
dpkg -l | grep linux-ubuntu-modules
```
and execute the command again with the version you'll have found.

---

### Post by thunderbirdje on 2011-09-09
> **TeoBigusGeekus said:**
> The specific version of linux modules (2.6.24-22) apply to the time the aforementioned thread was written - namely 2008.
Find the version of your linux modules
```
dpkg -l | grep linux-ubuntu-modules
```
and execute the command again with the version you'll have found.

Oh, I am sorry, forgot to adapt the command to the correct version. I have tried (with the same error):

```
sudo dpkg --reconfigure linux-ubuntu-modules-2.6.38-11-generic
```

The command ```
dpkg -l | grep linux-ubuntu-modules
``` results in nothing.

However ```
sudo dpkg -l | grep generic
``` results.

So I've tried ```
sudo dpkg-reconfigure linux-image-2.6.38-11-generic
``` because I have found out that it is now dkpg-reconfigure instead of dpkg --reconfigure :)

The configuration is done! I will try to boot into .11! I'll post the result.

---

### Post by thunderbirdje on 2011-09-09
It works! :popcorn:

Issuing the last commando fixed the kernel panic during boot time.

Thank you so much for pointing me in the right direction!

---

