---
title: "About Ubuntu says Maverick is Natty!"
date: 2011-03-12
forum: General Help
---

### Post by gobbles414 on 2011-03-12
I'm using Maverick Meerkat (with proposed and backport updates enabled), but About Ubuntu reports "You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012."

Did Ubuntu upgrade without to a pre-release version of Natty without my permission?

---

### Post by David D. on 2011-03-12
You did not get upgraded.  There is an uncorrected bug that causes About to report the wrong version.

---

### Post by cap10Ibraim on 2011-03-12
check the output of 
```

lsb_release -a

```

---

### Post by gobbles414 on 2011-03-19
Thank you both for your replies. Running lsb_release -a confirms that I am indeed running Maverick. Thanks again.

---

