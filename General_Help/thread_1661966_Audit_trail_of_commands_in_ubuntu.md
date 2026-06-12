---
title: "Audit trail of commands in ubuntu?"
date: 2011-01-07
forum: General Help
---

### Post by ramprasad1211 on 2011-01-07
Hi,

 I would like to log all the commands executed (in full) by all the users or alteast myself.

package lastcomm, doesn't store full command. 

Please help!

-ram.

---

### Post by seawolf167 on 2011-01-07
You mean 

```
vi ~.bash_history
```

---

### Post by drewsus on 2011-01-07
and the command "history" outputs that in terminal
furthermore, you can search for particular terms using grep and piping. For instance, if you wanted to search for things you have installed via terminal:
```
history | grep "apt-get install"
```

---

