---
title: "X Server does not load for the new kernel after updates"
date: 2011-01-14
forum: General Help
---

### Post by fordry on 2011-01-14
I just installed Ubuntu 10.10 64bit and manually installed the latest nvidia drivers. After doing that I did updates and trying to load the latest kernel results in it not booting into the graphical environment. It just gets to the command prompt with this message present until you hit enter "end_request: i/o error, dev sr0, sector 4096". Once I hit enter i can login and use the command prompt.

tried stopping and starting gdm but that makes no difference. Tried manually starting x and it won't start. Tried running nvidia-xconfig again and that didn't change anything. It does load just fine still using the older kernel that it installed with and It is properly using the graphics drivers near as i can tell (nvidia x server settings works and compiz advanced affects like the cube work fine). I'm just not sure what to do to fix the newer kernel problem.

---

