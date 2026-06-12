---
title: "Move command terminal"
date: 2010-02-07
forum: General Help
---

### Post by mohxinn on 2010-02-07
Hi, 

I am using Ubuntu 9.10. I was moving a theme folder to /usr/share/themes using the move command in terminal. I accidentally typed:
```
sudo mv theme-folder /usr/share/th
```

instead of:
```
sudo mv theme-folder /usr/share/themes
```

I can't find the theme folder anywhere. What happened to it? Any ideas

---

### Post by x33a on 2010-02-07
The folder got renamed to th and placed under /usr/share
try 
```
ls -l /usr/share/th
```

---

