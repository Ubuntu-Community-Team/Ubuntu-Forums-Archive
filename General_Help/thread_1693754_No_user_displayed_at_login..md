---
title: "No user displayed at login."
date: 2011-02-23
forum: General Help
---

### Post by dustyg54 on 2011-02-23
I made a clean install of 10.10 on an oldish desktop someone gave me. But after the first update, I can not login to the desktop environment. The login screen shows no user accounts, but other than that appears normal (purple background, ubuntu logo in white box mid-screen, and the options to shutdown, etc on the bottom bar).  The mouse works, however the pc will not shut down nor restart from the on-screen commands. 

Any help will be appreciated!

---

### Post by dustyg54 on 2011-02-23
Bump.  Any Ideas? Should I reinstall 10.10?

---

### Post by taojian on 2011-03-24
I'm having the same issue, also on an older laptop, a Lenovo. This has accompanied more and more full freeze-ups recently, though I don't know if those problems are related…

Are there likely to be log files somewhere that would have some information on what's going on?

Eric

---

### Post by 0b0bby0 on 2011-03-26
I´m having exactly the same problem. My computer freezed up (it became full of colerful streaks)  twice in last morning and after shutting it off I can only get to the exact same "login" schreen as referred to by previous poster. I could add one more thing though. In the middle it displays my computer name and when I klick it it switches to say ubuntu 10.10 and when I klick it again it switches back. Please help us. 
 
Thanks

---

### Post by Krytarik on 2011-03-26
Try re-installing "gdm":
```
sudo apt-get install --reinstall gdm
```
Greetings.

---

### Post by 0b0bby0 on 2011-03-27
I hit crtl + alt + F1 to get into the console at the place of the broken login schreen. There I could write my username and password and that part worked. When I type the code you gave me it doesn´t work and I get this back:
 
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct this problem.
 
 
Wierd. I´m new to linux and at this point I´m thinking that it´s better to just re-install the whole system. Of course I would prefer not to because it´s quite some work to re-configure the system again.

---

### Post by Krytarik on 2011-03-27
Then simply run that given command, it seems that a recent update of gdm hasn't been completed. No need to re-install it after that.

---

### Post by 0b0bby0 on 2011-03-28
Right. That was kindof obvious. I was expecting that it would open some file to edit and I thought that I wouldn´t know what to change. Everyting seems to be about editing files when you solve problems on linux. Anyways, that command worked, then I re-installed the gdm and now everyting is running great. Thanks a lot for your help! Saved me a bunch of hassle re-installing.

---

