---
title: "Creating another /tmp folder on 2nd HDD"
date: 2010-09-06
forum: General Help
---

### Post by KazaRgr on 2010-09-06
Hello everybody, i was wondering if anyone knows any trick to create a folder that deletes its contents on every boot, like "/tmp" but on a different hard drive since i have 2 internal hdd's.

[For saving massive temporary cache files, to increase overall speed (1 hdd for use, 1 hdd for storage/temp storage).]

Thanks in advance,
alex

---

### Post by Bachstelze on 2010-09-06
Just create a directory and make a cronjob to delete its contents at boot

```
@reboot rm -rf /foo/*
```

---

### Post by KazaRgr on 2010-09-06
thank u for ur fast response ):P

---

