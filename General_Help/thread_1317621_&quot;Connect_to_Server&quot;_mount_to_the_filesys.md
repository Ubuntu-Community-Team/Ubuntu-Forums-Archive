---
title: "&quot;Connect to Server&quot; mount to the filesystem?"
date: 2009-11-06
forum: General Help
---

### Post by wxl on 2009-11-06
looking [here]("http://http://ubuntuforums.org/showthread.php?t=300149") one finds the poster found a workaround.  tonight i found the solution:
```
~/.gvfs/server name
```

e.g. if you got a windows c drive shared on 192.168.1.253 you'd have
```
~/.gvfs/c on 192.168.1.253
```

weird!

---

