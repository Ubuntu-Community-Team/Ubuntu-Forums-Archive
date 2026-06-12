---
title: "Editing sudoers file"
date: 2011-09-18
forum: General Help
---

### Post by layr on 2011-09-18
Hey, i need my alarm-script work without sudoing.
Are these lines harmless in sudoers.tmp file?

```
# User privilege specification
root    ALL=(ALL) ALL
[B]user    ALL=NOPASSWD: /usr/sbin/rtcwake
user    ALL=NOPASSWD: /usr/sbin/pm-suspend[/B]

```

---

### Post by sisco311 on 2011-09-18
Not sure what do you mean when you say *harmless*. The bold lines will allow **user** to run the commands (rtcwake and pm-suspend) without a password. 

sudo reads the sudoers file and applies permissions in order from top to bottom. The last line in the file will overwrite any previous conflict with the config settings. So I'd put the new configuration lines at the bottom.

---

### Post by layr on 2011-09-18
Harmless as in whether and how malicious software could use pm-suspend and rtcwake against my system?
Thanks for the adding lines to the bottom of the file tip(Y)

---

