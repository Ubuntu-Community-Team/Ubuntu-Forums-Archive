---
title: "Window title bar not showing"
date: 2011-01-20
forum: General Help
---

### Post by irfan01 on 2011-01-20
Hello,
I using ubuntu 11.04
After ubuntu boot 2 seconds~, window title /bars\ not showing

Please help me.

Sorry for my bad English

---

### Post by irfan01 on 2011-01-21
Please help :(

---

### Post by tredegar on 2011-01-21
In a terminal 
```
metacity  --replace
```
will probably fix it.

---

### Post by stinkeye on 2011-01-21
If your using compiz as your window manager, use
```
gtk-window-decorator --replace
```which is the **window decorator** for compiz.



If you have enerald installed
```
emerald --replace
```will load emerald as the **window decorator**




```
metacity  --replace
```will switch your **window manager** to metacity




```
compiz --replace 
```will load compiz as your **window manager**

---

### Post by Lordestabia on 2011-05-02
This is not working. Even worse than 10.10 (slight problem) keeps dissapearing on all window managers (exception being KWin on occation). Beginning to regret upgrading to 11.04. Even interferes on the application bar on the bottom.

---

