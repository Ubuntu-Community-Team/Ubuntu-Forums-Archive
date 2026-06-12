---
title: "Update Manager Hangs"
date: 2010-09-11
forum: General Help
---

### Post by Cybrmerc on 2010-09-11
So recently I've been having trouble updating my package software. When I go to install the updates, the progress windows hangs until I 'force quit' the 'gksu' process. This happens through both update manager and synaptic. Any suggestions?

---

### Post by dcstar on 2010-09-11
> **Cybrmerc said:**
> So recently I've been having trouble updating my package software. When I go to install the updates, the progress windows hangs until I 'force quit' the 'gksu' process. This happens through both update manager and synaptic. Any suggestions?

Wait at least 5 minutes before losing patience.

If particular language translation files for your locale are not in the repository then you have to wait for the time out.

10.10 currently has this problem and while annoying it is not stopping the updates from eventually being processed.

---

### Post by wojox on 2010-09-11
What does it return when you run from the terminal:

```
sudo apt-get update; sudo apt-get upgrade
```

---

