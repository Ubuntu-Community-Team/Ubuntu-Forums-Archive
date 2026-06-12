---
title: "Tab autocomplete takes a long time"
date: 2011-02-13
forum: General Help
---

### Post by riksweeney on 2011-02-13
About a week ago I ran a script which extracted all the frames from a movie. It dumped all the files into my home directory and I deleted all (180,000+) of them.

Now when I try to do autocomplete by pressing tab in my directory, the process will freeze for about 30 seconds or so before completing.

I guess it still thinks the files are there or there's some sort of caching going on. Is there anything I can do to reset this?

---

### Post by ajgreeny on 2011-02-13
I'm not sure if this is a result of a huge file database that is being searched, but try ```
sudo updatedb
``` in terminal, which will do exactly what it suggests in the name, and then try the tab auto-completion again.

---

### Post by riksweeney on 2011-02-13
> **ajgreeny said:**
> I'm not sure if this is a result of a huge file database that is being searched, but try ```
sudo updatedb
``` in terminal, which will do exactly what it suggests in the name, and then try the tab auto-completion again.

Thanks, that did the trick! :D

---

