---
title: "Exit command won't work on Ubuntu 12.04"
date: 2012-09-24
forum: General Help
---

### Post by knightmetal on 2012-09-24
Hello,

Not sure what's happening but for several days the 'exit' command won't work in my terminal. I'm also having the same problem with MySQL. When I type the commands and hit enter all I see is a line break. I'm using Ubuntu 12.04. Any help, suggestions?

Thanks a lot.

ps please see attachment.

---

### Post by steeldriver on 2012-09-24
They are different problems I think

For mysql, you need to terminate each command with a semicolon

```
mysql> SHOW Databases;
```For the terminal I don't know - maybe you have a shell alias that's hiding the system definition of 'exit'?

---

### Post by daslinkard on 2012-09-24
> **knightmetal said:**
> Hello,

Not sure what's happening but for several days the 'exit' command won't work in my terminal. 
Have you tried in terminal going to Edit-Profile Preferences and  checking there ? 
Also try pressing Alt-F2 and in 'Run  Application'' enter 'gconf-editor' and click on 'Run'. 

Now go to  /apps/gnome-terminal/global and check your settings there (if you click  on each name on the right it gives a description of the action). 

Also  check /apps/gnome-terminal/profiles/Default/exit action is marked close  (you can change this with a right mouse click and select 'Edit key').

---

### Post by knightmetal on 2012-09-25
Thanks to both of you. I solved both problems.

@Steeldriver: I don't know why I couldn't spot the missing semi colon. That was the problem! although I'm pretty sure I did try using the semi colon before and some reason it didn't work the first time. Nevermind, that was the problem anyway! thanks.

@Daslinkard: yes I went to the Edit-Profile-Preferences and that's how I could solve it. The strange thing is that last week it was working fine, it happened suddenly, I never changed any settings. But again, the important thing is that I found the solution, thanks a lot.

---

### Post by daslinkard on 2012-09-25
Glad we were able to solve this together....please mark the thread as solved!  Any time you need anything we are here for you in the forum!

---

