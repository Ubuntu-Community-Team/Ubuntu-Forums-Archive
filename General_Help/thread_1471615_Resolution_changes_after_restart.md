---
title: "Resolution changes after restart"
date: 2010-05-03
forum: General Help
---

### Post by Shadow12313 on 2010-05-03
I set my resolution to 1680 x 1050 via the vendor's tool and I even saved it to the X config file but every time I restart it's set back to 1280 x 1024.  

Any ideas?

---

### Post by TeoBigusGeekus on 2010-05-03
If you're using nvidia, you should start the application with the terminal:
```
sudo nvidia-settings
```
in order to be able to save the changes permanently.

---

