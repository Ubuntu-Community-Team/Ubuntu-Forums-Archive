---
title: "Security - PAM Console User Equiv ??"
date: 2009-09-07
forum: General Help
---

### Post by FunkyRes on 2009-09-07
Coming from RH background.

We have a directory called

/etc/security/console.perms.d/

where we can customize some stuff.
For example, on CentOS I have a file called /etc/security/console.perms.d/51-custom.perms :

```

# device classes -- these are shell-style globs
<garmin>=/dev/ttyS0
<firewire>=/dev/fw0

# permission definitions
<console> 0600 <garmin> 0660 root.uucp
<console> 0600 <firewire> 0600 root.root

```

Whomever the PAM console user is then has ownership of those nodes.
What is the Ubuntu / Debian way to do that?

---

### Post by stanley82 on 2011-07-23
I do not see /etc/security/console.perms.d
in LinuxMint11 so I guess it's not in 11.04

---

