---
title: "How do i set my primary java?"
date: 2011-01-11
forum: General Help
---

### Post by Milkbone on 2011-01-11
i installed a new java and now need to set it as my primary one how would i do this?

---

### Post by ratcheer on 2011-01-11
See if you can run program update-java-alternatives

Tim

---

### Post by Milkbone on 2011-01-11
i seem to in terminal i get this 
```
usage: update-java-alternatives [--jre-headless] [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help

```

---

### Post by tredegar on 2011-01-11
Try```
sudo update-alternatives --config java
```

---

### Post by ratcheer on 2011-01-11
> **Milkbone said:**
> i seem to in terminal i get this 
```
usage: update-java-alternatives [--jre-headless] [--jre] [--plugin] [ -t|--test|-v|--verbose]
           -l|--list [<jname>]
           -s|--set <jname>
           -a|--auto
           -h|-?|--help

```

First run "update-java-alternatives -l" to list what javas your system has. Then, run "update-java-alternatives -s <jname>" where <jname> is the one you want from the output of the first command.

I'm not sure if you need to run this under sudo. You probably do need to run the -s command under sudo.

Tim

---

