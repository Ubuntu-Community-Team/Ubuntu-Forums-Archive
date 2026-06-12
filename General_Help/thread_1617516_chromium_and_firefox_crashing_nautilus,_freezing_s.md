---
title: "chromium and firefox crashing nautilus, freezing system"
date: 2010-11-09
forum: General Help
---

### Post by phobophilia on 2010-11-09
I've got a fun one for you. What makes absolutely any attempt to view a flash video crash Ubuntu 10.10, both in firefox and chromium? 
Lately, firefox began doing this. I switch to chromium, same thing. Also, the system completely locks up after about 30 minutes online if I can get the thing to work at all. When this happens, the rounded edges of all windows disappear, the menus become unresponsive, and any attempt to open the system monitor to end the offending process results in an "Unable to fork new process, system resource unvailable" something like that. 

My entire online routine goes like this: open terminal, su to admin account to enable ufw (which will not run at boot no matter what I try), su to normal, limited account, open web browser, things explode (or work for 15 minutes before freezing completely.) 

Help me, please!

---

### Post by HarrisonNapper on 2010-11-09
Firstly, when enabling ufw

```
sudo service ufw start
```

Secondly, have you tried completely removing and reinstalling flash? Are you running 32-bit or 64-bit?

---

### Post by phobophilia on 2010-11-09
Thanks for the command. This system is currently 32 bit, and what I've done so far is to completely remove any/all firefox related packages (which I assumed had flash in there) before installing chromium. To be honest, I haven't tried to fix flash so much as keep my system from freezing all the ever-loving time.

---

