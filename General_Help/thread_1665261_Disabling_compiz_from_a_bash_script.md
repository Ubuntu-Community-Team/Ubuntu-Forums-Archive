---
title: "Disabling compiz from a bash script"
date: 2011-01-12
forum: General Help
---

### Post by blazemore on 2011-01-12
Is it possible to do the following?
```

metacity --replace #Disable compositing
#Run an arbitrary command
compiz --replace #Enable compositing again

```

When I try this, the last line (compiz --replace) is run straight away without waiting for the second line to finish (It's "padsp", so might be reporting it has finished if it's a launcher for the wrapper, I have no idea), so compositing is enabled again straight away.

---

