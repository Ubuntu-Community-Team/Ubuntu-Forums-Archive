---
title: "[Karmic Koala] x2x"
date: 2009-10-31
forum: General Help
---

### Post by martijntje on 2009-10-31
I am trying to get x2x to work so I can share my mouse & keyboard. This used to work flawlessly in earlier versions of Ubuntu, but now I cannot get it to work.

```
ssh -X 192.168.1.100 "x2x -east -to :0.0"
No protocol specified
x2x - error: can not open display :0.0
```After searching around I found suggestions telling me to run either gdmsetup or edit /etc/gdm/gdm.conf . This is clearly meant for earlier versions of gdm, since gdmsetup now only allows me to set options for autologin. gdm.conf is gone and the closest I can find is gdm.schemas. I did change the default for security/DisallowTCP to false there, but without any effect. Restarted GDM, and after that even the entire computer.

Can anyone tell me how I can get my trusty x2x back to work?

---

### Post by martijntje on 2009-11-01
Anyone?

---

