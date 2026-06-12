---
title: "Restore Unity-greeter"
date: 2012-04-27
forum: General Help
---

### Post by b2zeldafreak on 2012-04-27
I installed UBuntu 12.04 yesterday, and it works great.

But when I installed the Kubuntu-desktop, it switched my login screen to the KDE login screen (which is very ugly), and I would like to change it back.

Can anyone tell me how to do this?

THanks,
b2zeldafreak

[U][B]found it 

[http://www.youtube.com/watch?v=tKkFVwHGY8I](http://www.youtube.com/watch?v=tKkFVwHGY8I)[/B][/U]

---

### Post by eco2geek on 2012-04-27
In a terminal, run:

```
sudo dpkg-reconfigure kdm
```

Enter your password. An explanatory text box will come up, telling you everything you need to know (but were afraid to ask) about display managers. Press "OK" and then choose "lightdm" instead of kdm as your display manager.

---

