---
title: "ibus and x restart"
date: 2012-07-02
forum: General Help
---

### Post by Pedroski55 on 2012-07-02
Hi! I need Chinese input, I use ibus-pinyin. Sometimes, on start up or restart, for reasons which are not clear to me, it is not there. I can call im-config, but it says, I must then restart x.

How do I restart x in Ubuntu 12.04?? Do I have to log out and then in?

I tried sudo restart gdm, sudo restart unity I get 'unknown job'

Thanks

---

### Post by ubudog on 2012-07-02
Try this, to restart the X server:
```
sudo service lightdm restart
```

---

### Post by Pedroski55 on 2012-07-02
That left me with a blackscreen

---

