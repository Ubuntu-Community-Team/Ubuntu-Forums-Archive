---
title: "remove a module"
date: 2010-06-13
forum: General Help
---

### Post by xinxinren on 2010-06-13
I found that a module, lp, is running in my ubuntu and I do not need it at all. I am trying to use rmmod (modprobe) to remove it. It removes it, however, it will be loaded again after reboot. Is there a way to remove it permanently? 

Thanks in advance.

---

### Post by quixote on 2010-06-15
I'm out of my depth here.  I don't know what you do to permanently remove it, but to keep it from being used on bootup, I think what you do is list it in the blacklisted modules, /etc/modprobe.d/blacklist.conf

---

### Post by bodhi.zazen on 2010-06-15
You can keep if from loading by blacklisting it. To remove it remove it you would need to compile a custom kernel (and not compile the module).

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by nothingspecial on 2010-06-15
[COLOR="Red"][SIZE="3"]Don`t just copy and paste this it moves the lp module to your home directory, and that is probably not a good idea[/SIZE][/COLOR]

However, as to your question on permanently removing a module....

You could do a ```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/char/lp.ko ~/
```

Then it wouldn`t load at boot because it wouldn`t be in the correct place.

It would probably hose your system though. Better to blacklist it.

But as this is linux, you are welcome to try it.

---

