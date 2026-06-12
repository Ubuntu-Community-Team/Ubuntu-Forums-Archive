---
title: "Update Manager Problem"
date: 2010-11-09
forum: General Help
---

### Post by oldposdells on 2010-11-09
Hi I'm having a problem with my Ubuntu 10.10. When ever I try to update it downloads the updates then when I click to install them it says "The installation or removal of a software package failed."
can any one tell me what the heck is going on. And it says the same thing when I try to install a program via Ubuntu Software Center.
PLEASE LET ME KNOW!!!!
Thanks.

---

### Post by Rubi1200 on 2010-11-09
Hi and welcome to the forums :)

How recently did you install 10.10 and have you updated the system at all since installing?

Go to Applications > Accessories > Terminal and run this command, posting back with any errors:

```
sudo dpkg --configure -a
```

Thanks.

---

