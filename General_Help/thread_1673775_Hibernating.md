---
title: "Hibernating"
date: 2011-01-22
forum: General Help
---

### Post by Psrj on 2011-01-22
So every time I try to hibernate Ubuntu 10.10 my computer goes to the screen saver but doesn't actually hibernate.  I know not all computers can hibernate on Ubuntu but is there anyway of checking which ones or is it just some system option or something I just overlooked that is causing my problems?

---

### Post by mikewhatever on 2011-01-22
I think you can look at the pm-powersave.log in /var/log.

---

### Post by Psrj on 2011-01-23
The file is huge.  What exactly would I be looking for?

---

### Post by mikewhatever on 2011-01-23
It's a log, and they tend to be verbose. Looking for errors might be useful.
You could also try hibernating, and after it fails, run **dmesg | tail -n 50**.
That should provide the last 50 messages that should be related to the failure.

---

### Post by HermanAB on 2011-01-23
Also note that for suspend to work at all, your swap partition must be at least 2x RAM size.

---

