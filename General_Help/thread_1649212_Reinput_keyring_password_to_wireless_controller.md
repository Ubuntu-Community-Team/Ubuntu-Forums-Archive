---
title: "Reinput keyring password to wireless controller"
date: 2010-12-19
forum: General Help
---

### Post by Vistro on 2010-12-19
When I used the LiveCD, it made me give it a password for the keyring, I made it lol, because it's a livecd session. 

After I installed, the wireless controller asked for the password again. I then changed it. When I installed Ubuntu previously, it didn't ask me for any of that, it just defaulted the keyring password to my user password or something like that and asked me if the wireless controller should have access ONCE. Now every time I boot I need to type the keyring password in again. How do I fix this?

---

### Post by tredegar on 2010-12-20
Delete everything in **~/.gnome2/keyrings**
Next time it asks for a keyring password, leave it blank.

---

