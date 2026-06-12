---
title: "How to set ALL of konsole transparent?"
date: 2006-06-11
forum: General Help
---

### Post by SimonTheMime on 2006-06-11
got it, thanks

---

### Post by FizDev on 2006-06-11
Just in case other people are asking themselves about it... you could (I think) do it this way :
Open a terminal and type
```
sudo apt-get install eterm
```
Then press Alt+F2 and run 
```
Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=80x52+30+30 --foreground-color=white
```

---

