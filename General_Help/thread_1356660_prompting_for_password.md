---
title: "prompting for password"
date: 2009-12-16
forum: General Help
---

### Post by shaon3343 on 2009-12-16
[SIZE=3][B]hi there, 
I used ubuntu 9.04 for last 5 months, and i've switched to ubuntu 9.10 a few days back. In ubuntu 9.04 when i double clicked any drive it opened immidiately but now in ubuntu 9.10 it is prompting me for my password!! In ubuntu 9.04 when i right clicked any folder there was an option saying "open as administrator" but in this 9.10 there is no such option. So how can I fix those problems? please help me.[/B][/SIZE]

---

### Post by philinux on 2009-12-16
> **shaon3343 said:**
> [SIZE=3][B]hi there, 
I used ubuntu 9.04 for last 5 months, and i've switched to ubuntu 9.10 a few days back. In ubuntu 9.04 when i double clicked any drive it opened immidiately but now in ubuntu 9.10 it is prompting me for my password!! In ubuntu 9.04 when i right clicked any folder there was an option saying "open as administrator" but in this 9.10 there is no such option. So how can I fix those problems? please help me.[/B][/SIZE]

For open as admin you need to install

```
sudo apt-get install nautilus-gksu
```

Then log out then in.

---

