---
title: "How to solve Wine problems after changing username"
date: 2012-01-28
forum: General Help
---

### Post by ryanmichaelmcclure on 2012-01-28
I had my username as "ryan" on my system, but changed it to "ryanmcclure" because I wanted to see that. However, after doing this, Wine was unable to open programs or some programs crashed. I couldn't find any solutions on the forums for this, so I thought I would post the solution for anyone else with this problem:

Go to c:/users/username and change the locations of the files to match your new username.

Then go to .wine and open system.reg, user.reg, and userdef.reg. Replace <old username> with <new username> and save them all. Reboot your system, and the problems go away. :)

This isn't probably the right place for this thread, but I wanted to put this here so those with this problem can have a solution.

---

