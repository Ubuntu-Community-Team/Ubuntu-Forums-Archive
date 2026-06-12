---
title: "upgraded to 12.04 now can't get into GUI"
date: 2012-05-05
forum: General Help
---

### Post by upjeeper on 2012-05-05
last week I upgraded my ubuntu to 12.04 as the system asked
i haven't used it since. today when i booted it would ask for my password, i've give it, then it would get to a blue desktop screen and hang. i can reboot by pressing the power button (on my laptop) but can't seem to get anything to work

any suggestions please?

machine specs:
- dual core toshiba laptop
- 4gb of ram
- 250gb hard drive

---

### Post by hal8000 on 2012-05-05
When you cant login, can you access the console
?
Trl ctrl-alt-F1

Login with username and password and then start with:
startx

---

### Post by upjeeper on 2012-05-06
> **hal8000 said:**
> When you cant login, can you access the console
?
Trl ctrl-alt-F1

Login with username and password and then start with:
startx

thanks, i tried that, then run startx from the console
got the following message:

[I]"fatal server error: server is already active for displace 0
if this server is no longer running, remove /tmp/.X0-lock and start again"
[/I]

---

### Post by upjeeper on 2012-05-06
ah ha! i just had to hold the shift key on the left side of the keyboard when booting, then do a rebuild of the packages
that fixed whatever was wrong with it

---

