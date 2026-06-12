---
title: "Need Help Fast...Urgent !!"
date: 2010-06-30
forum: General Help
---

### Post by SlyPinguin on 2010-06-30
Ok, Big Problem.... Tried install new update on Ubuntu 10.04 and the following output appears: --'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'-- It also appears when I do it through the Terminal.......... Yes, weird I know!! It also does it every time I try to update something (in terminal also) ..It started doing this recently so help!!!!!!! What is it and how to fix it and/or get it out??:confused:      

Super Big Thanks!!!

---

### Post by patchwork on 2010-06-30
One of the lines in the file that defines your repositories is apparently incorrect.
Have you recently added or changed your repositories (Software Sources)?

Please post the output of ```
cat /etc/apt/sources.list
```

---

