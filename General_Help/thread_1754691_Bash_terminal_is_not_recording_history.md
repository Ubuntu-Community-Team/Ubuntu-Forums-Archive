---
title: "Bash terminal is not recording history"
date: 2011-05-10
forum: General Help
---

### Post by msjones on 2011-05-10
This is probably a quick simple fix but I couldnt find anything.

Every time I exit terminal sessions my history is wiped, how can I stop this? I am running a fully updated install of 10.10.

Thanks

---

### Post by Dave_L on 2011-05-10
Is the file ~/.bash_history owned by you?

```
stat ~/.bash_history
```

---

