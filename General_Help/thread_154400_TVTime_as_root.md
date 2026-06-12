---
title: "TVTime as root?"
date: 2006-04-03
forum: General Help
---

### Post by nismoskys on 2006-04-03
i recently half-assed the install of mythtv//i started it but didnt really finish it..

but now.. if i try to use TVtime i get a blue screen in the tvtime window saying

```
No Video Source

No Signal

Permission Denied

Cannot open capture device /dev/video0
```


but if i open up a terminal and go
```
sudo tvtime
pwd
```
it works fine.

any reason why i suddenly need root to watch tv?
or how can i just set the tvtime icon in the apps menu in gnome to just start as root?

thnx

---

### Post by vruum on 2006-04-03
mythtv might have, for whatever reason, changed the permissions on /dev/video0, try, in a terminal <code>ls -l /dev/video0 </code> also, it might be that something like the mythtv-backend is running, if you're not gonna use mythtv make sure it's completely uninstalled.

---

### Post by nismoskys on 2006-04-03
cool thnx..
its not that i dont want to use mythtv.. i just cant find a decent guide on how to install it.. i found one a while ag, but dont have the link anymore..

---

