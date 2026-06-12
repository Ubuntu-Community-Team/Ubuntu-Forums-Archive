---
title: "I remove PSAD, but e-mails don't stop. Please help me!"
date: 2011-03-07
forum: General Help
---

### Post by testme26 on 2011-03-07
Hello community ubuntu i need your help.

I install in my ubuntu server 8.04 psad for tested. But after i  autoremove this software. The problem is i continue to recieve e-mails  from software.

Someone can help me tell me how stop e-mails from psad software? 

Thank you very much!

---

### Post by testme26 on 2011-03-07
Please help me... I recieve now 300 emails from this script!!!

I'm desperate!

PSAD: [http://www.cipherdyne.org/psad/](http://www.cipherdyne.org/psad/)

Please help me stop this emails!

---

### Post by Habitual on 2011-03-07
check crontab with ```
crontab -l
``` <- that's a lower case L)
also, paste the contents of /etc/psad/psad.conf using 
```
gksu gedit /etc/psad/psad.conf
```
and paste the results or both of those here.

Thank you.

---

### Post by testme26 on 2011-03-08
> **Habitual said:**
> check crontab with ```
crontab -l
``` <- that's a lower case L)
also, paste the contents of /etc/psad/psad.conf using 
```
gksu gedit /etc/psad/psad.conf
```and paste the results or both of those here.

Thank you.

Thank you for you repley.

In crontab i have just "Webmin".

I remove directory psad from etc :S

---

### Post by Habitual on 2011-03-08
Maybe you should have de-installed it instead of just removing /etc/psad ?

I suggest re-installing it, then de-installing it with a --purge option
```
sudo apt-get install psad
``` 

then
```
sudo apt-get remove --purge psad
```
then
```
sudo apt-get autoremove
```

Please let us know...

---

### Post by testme26 on 2011-03-08
I make this:

sudo apt-get autoremove psad

And "reboot now" the server.

---

### Post by testme26 on 2011-03-09
It's possible in sendmail block root@domain send emails?

---

### Post by Habitual on 2011-03-09
Are the emails literally root@domain?
Because if they are, that indicates to me that the /etc/psad/psad.conf is still being 'read' somehow.

Does that file still exist?

I'd like you to check the starting of the psad services by installing chkconfig.

```
sudo install -y chkconfig
```
then
```
chkconfig | grep -i psad*
```

Please let us know...

---

### Post by testme26 on 2011-03-09
I use ubuntu 8.04

I make your command i give me a error:

root@xxx:~# sudo install -y chkconfig
install: invalid option -- y
Try `install --help' for more information.

---

### Post by oldos2er on 2011-03-09
> **testme26 said:**
> I make this:

sudo apt-get autoremove psad

And "reboot now" the server.

You need to use remove or purge in place of autoremove.

---

