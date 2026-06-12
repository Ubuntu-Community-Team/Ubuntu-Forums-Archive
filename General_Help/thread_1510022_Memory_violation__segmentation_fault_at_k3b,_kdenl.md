---
title: "Memory violation / segmentation fault at k3b, kdenlive and wine"
date: 2010-06-15
forum: General Help
---

### Post by WebNuLL on 2010-06-15
Hello, i cant run k3b, kdenlive and wine.
When i try to run some of listed apliactions i got **segmentation fault**.

Here are some logs:

strace k3b
[http://wklej.org/id/350797/](http://wklej.org/id/350797/)

valgrind k3b
[http://wklej.org/id/350806/](http://wklej.org/id/350806/)

strace kdenlive
[http://wklej.org/id/350801/](http://wklej.org/id/350801/)

valgrind k3b
[http://wklej.org/id/350807/](http://wklej.org/id/350807/)

I launched Wine separated version installed by PlayOnLinux, and just made a bash script in /usr/bin/wine:

```
#!/bin/bash
/home/webnull/.PlayOnLinux/WineVersions/1.1.44/usr/bin/wine $@
```

And wine runs from /home/webnull/.PlayOnLinux/WineVersions/1.1.44/usr/bin/win using /usr/bin/wine but this is not a solution, its just a shortcut to other installed wine.

Im using ArchLinux, kernel 2.6.34-1, please help - thank you!

-- WebNuLL

---

