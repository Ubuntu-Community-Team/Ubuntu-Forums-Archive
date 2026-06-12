---
title: "GRUB Blinks, Throws &quot;Error: Not a Directory&quot; Message"
date: 2009-11-30
forum: General Help
---

### Post by sog on 2009-11-30
After a routine update of my Thinkpad X40, running Karmic, I'm now unable to log in to the machine. 

Description:
Machine does not autoboot, but redirects without prompting to normal GRUB (1.96) menu. Normal, except that the highlighted selection in the GRUB menu blinks on and off. Every selection from 2.6.31-15-generic to memtest86+ (including the recovery options) returns the same error when it's selected:

```
error: not a directory

Press any key to continue...
```

Which kicks you right back to GRUB. 

Attempted:
Booted up with a LiveCD, fscked the /dev/sda1 partition and it came back clean. 

Other than that, I'm at a loss. I can reimage the machine if necessary, but I'd prefer not to if it can be avoided. 

Any ideas?

---

