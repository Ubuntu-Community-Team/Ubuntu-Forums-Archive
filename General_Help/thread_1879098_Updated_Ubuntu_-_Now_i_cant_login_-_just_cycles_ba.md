---
title: "Updated Ubuntu - Now i cant login - just cycles back to login screen after i try"
date: 2011-11-10
forum: General Help
---

### Post by 5tr34k on 2011-11-10
Hey Guys

So i have Ubuntu on my laptop, and i just installed a bunch of updates (havent been on in a while).

I restarted when prompted, and now i cant login.

I enter my information on  the login screen, and it looks like it will go to the desktop, but it doenst.  it goes to a black screen, and then back to the login screen.

i can log in at the command prompt, so my info is correct.

Things i have tried:

update-alternatives --config x-session-manager
startx
rm -rf /tmp/.X0-lock


startx -- :1



 ps aux | grep `cat /tmp/.X0-lock`




and a bunch of other commands i dont understand! 


If anyone could help it would be aweomse.
i can get into the root user, and my user from the command screen, but i cant login with the GUI.

---

