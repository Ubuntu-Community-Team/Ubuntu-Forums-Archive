---
title: "No GUI"
date: 2012-02-20
forum: General Help
---

### Post by beatbum on 2012-02-20
I have loaded ubuntu onto a HP Pavilion dv6 Laptop using Wubi. I have had to do the nomodeset solution to fix the initial problem. My new problem is that the GUI does not launch and leaves only what I believe to be the console or terminal. I am able to enter my name and password to this console but do not have any knowledge of what to do. Any help will be greatly appreciated.

---

### Post by HeroOfCanton on 2012-02-20
Try:

```
sudo /etc/init.d/gdm start
```or just

```
startx
```

---

