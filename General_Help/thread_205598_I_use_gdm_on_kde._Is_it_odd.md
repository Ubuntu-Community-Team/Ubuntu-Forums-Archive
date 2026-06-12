---
title: "I use gdm on kde. Is it odd?"
date: 2006-06-28
forum: General Help
---

### Post by barisurum on 2006-06-28
Hello. I use kde as desktop, but the display manager is gdm. does it cause any problems?

    And every application creates backup files. I dont want them to do so. How can I change it on kde?

    Thankx

---

### Post by dabear on 2006-06-28
[QUOTE=barisurum]Hello. I use kde as desktop, but the display manager is gdm. does it cause any problems?

    And every application creates backup files. I dont want them to do so. How can I change it on kde?

    Thankx[/QUOTE]
1) Won't cause any problems. You can change it back to kdm by doing a 
```
dpkg-reconfigure kdm
```

---

### Post by user1397 on 2006-06-28
[quote=dabear]1) Won't cause any problems. You can change it back to kdm by doing a 
```
dpkg-reconfigure kdm
```[/quote]actually you have to run it with root privileges, so ```
sudo dpkg-reconfigure kdm
```

[quote=barisurum]     And every application creates backup files. I dont want them to do so. How can I change it on kde?[/quote]i have been asking myself that same question for ages.... it probably has to do with konqueror's settings, but i have been too lazy to try :(

---

