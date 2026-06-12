---
title: "Clear History"
date: 2009-12-07
forum: General Help
---

### Post by tushar.hiwse on 2009-12-07
Hi,
 
Can anybody tell me how to clear the history in linux ?
 
#history
 
Regards,
Tushar :P

---

### Post by Vishnu V on 2009-12-07
There is a hidden file in your home folder named .bash_history
You can clear it

file contains roots history is
/root/.bash_history

---

### Post by alienclone on 2009-12-07
```
history -c
```

---

### Post by wilee-nilee on 2009-12-07
If your trying to clear unneeded stuff and cache run in the terminal.
sudo apt-get autoremove
then
sudo apt-get autoclean

---

