---
title: "Can't login"
date: 2012-02-15
forum: General Help
---

### Post by Cavid on 2012-02-15
Hello people. I am having a problem with logging in to Kubuntu 11.10. I was updating my system via muon, but it stuck at 57%, so turned my laptop off (Shutting down from menu didn't work, so I hold down shut down button until it turned off). When turned my laptop on today, instead of regular login screen, there was a black screen, with my laptops's name and asking for login. But it doesn't seem to recognize my login, I typed it like hundred times, but everytime it says, incorrect. What login I might be asked for? Or is there any other way to log in? 

Thanks in advance!

---

### Post by McNils on 2012-02-15
boot into recovery mode and complete the upgrade. Plug in the network cable. 

```
apt-get install -f
dpkg --configure -a
```

---

### Post by Cavid on 2012-03-14
Thanks, solved :D

---

