---
title: "how can I run a script after returning from suspend mode?"
date: 2010-02-05
forum: General Help
---

### Post by spear1bearer on 2010-02-05
Greetings,

I have a Bash script that runs on my system every time I log in. It mostly remaps my keyboard with xmodmap. However, whenever my computer is suspended, my settings are undone. So, every time I resume from standby and type in my password, I have to open a terminal and run my script. Since I do this a few times a day, it has become a big nuisance. 
I would like to know if I could somehow automate this by using some user-specific config file in Ubuntu/gnome. I have tried .xinitrc, .xsession, .Xmodmap and some others, but none seem to be doing the trick. I also ruled out acpi and rc# scripts, because I only want the settings to apply to a single user account.

---

