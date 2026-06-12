---
title: "Automatic login fails due to missing information"
date: 2011-06-16
forum: General Help
---

### Post by davidryderuk on 2011-06-16
Hi,
After changing my user's UID number with the "usermod -u" command or otherwise changing the login settings my computer no longer logs in automatically. I can login manually by selecting the "Other" option and manually typing in my user-name and password. However my user-name is gone from the list of users at the login screen or in the Login Screen Settings program. 

Other than that my computer seems to function fine. My users details are still listed in "User settings".

---

### Post by davidryderuk on 2011-06-16
I managed to find a way round the problem by doing the following:

1. I edited the GDM configuration file
```
sudo gedit /etc/gdm/custom.conf
```

2. I added my username to the file by changing

> AutomaticLogin=

to 

> AutomaticLogin=username

I still can't work out why my user-name isn't listed properly, but I guess the problem is solved.

---

