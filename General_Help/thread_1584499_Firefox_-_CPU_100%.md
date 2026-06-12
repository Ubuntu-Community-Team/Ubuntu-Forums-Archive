---
title: "Firefox - CPU 100%"
date: 2010-09-29
forum: General Help
---

### Post by HannuMR on 2010-09-29
What is the reason, that again only with Firefox CPU stays 100%, and only reboot computer helps? Same was before with other distros.
Linux Mint users notice the same.

Firefox 3.6.10, Ubuntu 10.04.1

---

### Post by philinux on 2010-09-29
> **HannuMR said:**
> What is the reason, that again only with Firefox CPU stays 100%, and only reboot computer helps? Same was before with other distros.
Linux Mint users notice the same.

Firefox 3.6.10, Ubuntu 10.04.1

Not happening to me. Could be addon related. Try running in safe mode first.

Open a terminal.

```
firefox -safe-mode
```

Also no need to reboot. 

```
killall firefox-bin
```

Or use System Monitor to kill any firefox processes.

---

### Post by HannuMR on 2010-09-29
OK Philinux
I must watch, because it is not often.
By System Monitor it is easy.

---

### Post by lovinglinux on 2010-09-29
Could be flash content. Check how much CPU cycles is plugin-container process using.

It is also possible that an extension is performing some heavy function, specially if it is database related. Does the problem persist in safe mode? Do you notice excessive disk activity at the same time the CPU reaches 100%?

---

