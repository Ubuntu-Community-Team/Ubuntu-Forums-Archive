---
title: "Added AD Group to Sudoers, still can't modify system configuration"
date: 2012-09-28
forum: General Help
---

### Post by llemar97 on 2012-09-28
Greetings,

I have a Ubuntu 12.04 device that I added to Active Directory via Likewise-Open-GUI.

I also went into the sudoers file and added the AD group (that my username is a member of) underneath the line:

> %admin ALL=(ALL) ALL

I can do sudo commands in the CLI with no issue, however, if I try to use an app like GParted or Synaptic, I get a prompt saying...

> You need to authenticate to modify the system configuration

I can add my individual login name to the sudo group and that resolves this issue, but how do I add an **Active Directory group** to the sudo group?

---

### Post by llemar97 on 2012-10-09
I also get prompted for administrator credentials when I try to add a printer.

Does anyone out there have experience with these issues?

---

### Post by capscrew on 2012-10-10
> **llemar97 said:**
> I also get prompted for administrator credentials when I try to add a printer.

Does anyone out there have experience with these issues?
Linux groups can only hold usernames.  See ```
man group
```

---

