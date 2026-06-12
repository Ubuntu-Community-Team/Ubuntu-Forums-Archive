---
title: "apt-get command without needing user to type Y to confirm"
date: 2010-01-07
forum: General Help
---

### Post by wbrady4927 on 2010-01-07
I am writing an installation script that installs several packages using apt-get. Is there a way to run that command with some sort of option that makes it so the user doesn't have to type Y to confirm the installation? The user needs to be run the script as sudo already. Any ideas are welcomed!

---

### Post by philinux on 2010-01-07
> **wbrady4927 said:**
> I am writing an installation script that installs several packages using apt-get. Is there a way to run that command with some sort of option that makes it so the user doesn't have to type Y to confirm the installation? The user needs to be run the script as sudo already. Any ideas are welcomed!

Yes with -y switch. Open a terminal and have a read.

```
man apt-get
```

Or System>help and support, search apt-get.

---

### Post by wbrady4927 on 2010-01-07
Thanks I completely missed that earlier when going through the man page. There is a -y option that assumes "yes" as answer to all prompts.

---

