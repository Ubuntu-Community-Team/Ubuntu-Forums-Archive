---
title: "info about /etc/sudoers"
date: 2012-02-15
forum: General Help
---

### Post by jacob.david on 2012-02-15
In my default /etc/sudoers file I have the following

```
# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

```

What is the difference between (ALL:ALL) and (ALL)?

---

### Post by aeiah on 2012-02-15
ALL:ALL will refer to username:group in this context i think

---

### Post by jacob.david on 2012-02-15
That doesn't look quite right. If (ALL) can be used to execute the commands as any user then why bother with (ALL:ALL). There must be something different about this. Although I too believe it must be something to do with group.

---

### Post by emorkay on 2012-02-15
See this...will be useful
[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

