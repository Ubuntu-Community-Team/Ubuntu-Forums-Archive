---
title: "Can't find pure-ftpd.conf"
date: 2012-03-19
forum: General Help
---

### Post by hunterlove22 on 2012-03-19
I installed pure-ftp on Ec2 Ubuntu. But I can not find the pure-ftpd.conf. I have problem with Passive Port. Trying to find configuration file to enable Passive Port. Does anyone know this issue?

Thanks!

---

### Post by raja.genupula on 2012-03-19
please see this 


[http://manpages.ubuntu.com/manpages/hardy/man8/pure-ftpd-wrapper.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pure-ftpd-wrapper.8.html)

[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

---

### Post by hunterlove22 on 2012-03-19
I dont think that work. I have to enable PassiveMode and Limite Active mode in my Filezilla. That works perfectly. Btw, thanks!

---

### Post by raja.genupula on 2012-03-19
but i am sure with this 

[http://wiki.filezilla-project.org/Network_Configuration](http://wiki.filezilla-project.org/Network_Configuration)

---

### Post by wojox on 2012-03-19
Should be in /etc/proftpd/proftpd.conf

---

### Post by raja.genupula on 2012-03-19
> **wojox said:**
> Should be in /etc/proftpd/proftpd.conf

Hi Friend 
          Actually @OP asking pure-ftpd.conf so i have given the man page of it too and in that description  its already mentioned as  ```
/etc/pure-ftpd/conf
``` is the location but user said its not what he wants and i am also not expert in this area , so please help him on this issue .  
                                   Thank you .

---

### Post by wojox on 2012-03-19
> **raja.genupula said:**
> Hi Friend 
          Actually @OP asking pure-ftpd.conf so i have given the man page of it too and in that description  its already mentioned as  ```
/etc/pure-ftpd/conf
``` is the location but user said its not what he wants and i am also not expert in this area , so please help him on this issue .  
                                   Thank you .

pure-ftpd not proftpd. Gotcha. :KS

---

