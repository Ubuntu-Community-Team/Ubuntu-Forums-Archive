---
title: "Cant able to enable my firewall.."
date: 2010-04-03
forum: General Help
---

### Post by karthick87 on 2010-04-03
I cant able to enable my firewall,when i enable it gives me an error. 

 ```

 karthick@Learners-desktop:~$ sudo ufw enable  
 ERROR: Couldn't stat '/etc/ufw/after6.rules'  
 karthick@Learners-desktop:~$ sudo ufw disable  
 ERROR: Couldn't stat '/etc/ufw/after6.rules'  
 karthick@Learners-desktop:~$ sudo ufw status  
 ERROR: Couldn't stat '/etc/ufw/after6.rules'  
 karthick@Learners-desktop:~$ sudo ufw restart  
 
```
 

 Is it possible to remove ufw completely and reinstall it again?If so pls tell me the procedure to do it.

---

### Post by karthick87 on 2010-04-04
I have removed ufw and reinstalled again,now the problem was solved.

---

