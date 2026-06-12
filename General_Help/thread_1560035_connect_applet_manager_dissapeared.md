---
title: "connect applet manager dissapeared"
date: 2010-08-24
forum: General Help
---

### Post by borabora1 on 2010-08-24
Dear all, 

Seems like i can't get it to the desktop bar, and impossible to reinstate it from the menu connections networks from system. 
Also, command typed : alt +F2: nm-applet & doesn't reinstate it.

Thanks for your comments and suggestions on that

---

### Post by clrg on 2010-08-24
What happens if you

```
sudo service network-manager start
```

and errors do you get when executing

```
nm-applet
```
(without the ampersand sign)

Also, try adding network-manager to your panel using the GUI (right-click, Add to panel...)

---

### Post by borabora1 on 2010-08-24
I am afraid i do not have the GUI inside the options for the panel.
Also direct commant as request were not denied, and accepted by system but nothing happened to the panel.

System can still connect to previous wifi in memory of network connection, but as the network manger is not active no now connections can be activated in different locations. 

Thanks for your answer up here,

---

