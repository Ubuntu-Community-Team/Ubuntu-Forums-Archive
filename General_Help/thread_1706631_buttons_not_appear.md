---
title: "buttons not appear"
date: 2011-03-14
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-14
Hi 

I cant see any closing ,Minimize,Maximization buttons on any window 

I had replaced my monitor with other crt 

am  closing by using alt f4 and from file quit now 



thanks

---

### Post by stinkeye on 2011-03-14
If your using compiz Press alt + F2 and run
```
compiz --replace
```

Still doesn't show titlebar, try
```
gtk-window-decorator --replace
```


If your using the default metacity window manager, try
```
metacity --replace
```

---

### Post by Rakeshvijayan on 2011-03-14
> **stinkeye said:**
> If your using compiz Press alt + F2 and run
```
compiz --replace
```Still doesn't show titlebar, try
```
gtk-window-decorator --replace
```If your using the default metacity window manager, try
```
metacity --replace
```

Thanks for your quick replay I had worked with compiz that the problem 

another  problem arise compiz is not working ,how can i rotate my desktop the compiz icon appeared on my panel

---

### Post by stinkeye on 2011-03-14
The icon is for **fusion-icon** which allows you to change your window manager and decorator.
If you have enabled the proprietary drivers for your video card 
you should be able to adjust your compiz settings with **compizconfig-settings-manager**.
Search in the Ubuntu Software Centre for **ccsm**.
Enable the **desktop cube** and **rotate cube** plugins.

---

