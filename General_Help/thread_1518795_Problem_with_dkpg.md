---
title: "Problem with dkpg"
date: 2010-06-27
forum: General Help
---

### Post by Peppuzzo on 2010-06-27
I got this problem with Synaptic, and now I cannot install or upgrade. Whatever I try, I get this error message:

```

dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'gnokii' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

```

I have tried to completely remove or add gnokii, without success...Any suggestion?

---

### Post by dino99 on 2010-06-27
is there broken package(s) into synaptic ?

[http://ubuntuforums.org/showthread.php?t=679113](http://ubuntuforums.org/showthread.php?t=679113)

---

### Post by gmargo on 2010-06-27
Manually edit the file **/var/lib/dpkg/statoverride** (make a backup!) and remove the line that references gnokii.  Then try again.

---

