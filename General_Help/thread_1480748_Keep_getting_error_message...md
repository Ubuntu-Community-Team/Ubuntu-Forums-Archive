---
title: "Keep getting error message.."
date: 2010-05-11
forum: General Help
---

### Post by Mdhall7477 on 2010-05-11
It reads  dpkg was interrupted you must run sudo dpkg manually to correct problem. I tried the terminal options and still nothing.. The thing is I am trying to install other packages and it says have to close that one out first... Need help...Please....

---

### Post by lisati on 2010-05-12
If you have the software center or synaptic package manager open, close them first. Then go to Applications->accessories->terminal and run the following:
```
sudo dpkg --configure -a
```
It will ask for your password, which will not show as you type but will still be accepted.

Once the command has completed without error, try what you were doing again.

Feel free to let us know how you get on.

---

