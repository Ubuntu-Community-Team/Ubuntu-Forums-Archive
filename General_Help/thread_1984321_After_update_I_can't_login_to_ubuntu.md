---
title: "After update I can't login to ubuntu"
date: 2012-05-21
forum: General Help
---

### Post by stirith on 2012-05-21
Hi,

I installed new ubuntu 12.04, and I installed some software..After restart computer I can't login to the account...I clicked to my account i a try login...ubuntu go to the black site and back to the login page. When I can another login it is the same.. Ubuntu haven't any errors... This problem is only one account. If I make new admin account - I can login for this... I configured all day account and I don't want lose this account.

Please help me

---

### Post by stirith on 2012-05-22
any idea ?

---

### Post by raja.genupula on 2012-05-22
At login screen type CTRL+ALT+F1 and login there then type as 

```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

