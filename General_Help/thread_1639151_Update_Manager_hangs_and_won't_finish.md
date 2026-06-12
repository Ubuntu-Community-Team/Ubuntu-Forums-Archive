---
title: "Update Manager hangs and won't finish"
date: 2010-12-06
forum: General Help
---

### Post by A_T on 2010-12-06
Ever since I installed Maverick Update Manager it hangs when I update and I eventually have to kill it. Anyone else had this problem and solved it?

---

### Post by sikander3786 on 2010-12-06
It hangs when installing some updates or it just hangs when you start it?

We need to see the complete output of these commands.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

You can wrap your outputs with proper code # tags from post menu thus make them easier to read ;-) [/code] at the end [code] at the beginning.

---

### Post by A_T on 2010-12-06
Hi those commands produce no errors - apt-get works fine as does aptitude and also synaptic. The problem seems specific to update-manager - it launches fine but hangs after updating or upgrading.

---

### Post by sikander3786 on 2010-12-06
Output of above mentioned commands...?

Try starting update-manager from Terminal and see if it throws some errors there when it gets stuck. If yes, post those.

```
update-manager
```

Re-installation of update-manager is another option.

---

