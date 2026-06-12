---
title: "Desktop launcher for yWriter 5"
date: 2010-08-31
forum: General Help
---

### Post by erhey on 2010-08-31
Hi,

I'm trying to create a desktop launcher for yWriter 5, which works through Mono. The only way I can launch it now is to open the terminal and enter cd ~/yWriter5/bin/ then mono yWriter5.exe. I can't seem to figure out how to create a desktop shortcut. When I try to create a launcher with the command mono yWriter5.exe, it does nothing. I also tried opening yWriter with Wine but that doesn't work either. 

Any ideas?

Thanks

---

### Post by cemacmillan on 2011-04-23
If you haven't yet resolved the problem, add a customized launcher with:

mono <full path to yWriter5 executable, including the ".exe"> 

and you should be good to go.

(found your post while searching for an icon for same)

> **erhey said:**
> Hi,

I'm trying to create a desktop launcher for yWriter 5, which works through Mono. The only way I can launch it now is to open the terminal and enter cd ~/yWriter5/bin/ then mono yWriter5.exe. I can't seem to figure out how to create a desktop shortcut. When I try to create a launcher with the command mono yWriter5.exe, it does nothing. I also tried opening yWriter with Wine but that doesn't work either. 

Any ideas?

Thanks

---

