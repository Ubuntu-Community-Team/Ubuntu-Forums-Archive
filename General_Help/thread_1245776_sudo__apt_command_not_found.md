---
title: "sudo : apt: command not found"
date: 2009-08-20
forum: General Help
---

### Post by oboedad55 on 2009-08-20
I type "sudo apt remove" and get "sudo : apt: command not found". Using "aptitude" works. Any ideas?

Thanks,
Jon

---

### Post by doas777 on 2009-08-20
```
sudo apt-get remove <appname>
```

I think of apt as a superset of several programs, including apt-get. I don't think apt is itself an application. just use the remove option for apt-get

---

### Post by oboedad55 on 2009-08-20
> **doas777 said:**
> ```
sudo apt-get remove <appname>
```

I think of apt as a superset of several programs, including apt-get. I don't think apt is itself an application. just use the remove option for apt-get

Aha! Okay, thanks for the reply!

Jon

---

