---
title: "Kubuntu crash while updating! :("
date: 2011-05-12
forum: General Help
---

### Post by shekhil on 2011-05-12
hi.. 

I was using kubuntu 9. (forgot the correct version) , and i tried to update by system using command prompt. In between something happened and update got stuck. When I restarted, Its now showing 'ubuntu 10.4 loading' and then it showed not able to mount,Skip using S or mount manually using M. 
When I pressed M, I got one command prompt. Now what can I do to get things back. :( I want to atleast copy my datas to my hard disk. Its showing read only file system, ommitted copying.. What to do..Please help :( :( Asap...My exams are apporaching..:(:confused:

---

### Post by shekhil on 2011-05-14
pls help......
advance thanks...

---

### Post by wilee-nilee on 2011-05-14
Login at the prompt and run this command it is for unlocking the stalled upgrade it may start up so be connected to the net.
```
sudo apt-get -f install
```

If your getting to the grub menu choose recovery then in the gui choose net root be plugged to the net, and login I believe as well, then run the command without sudo you will be in root already.

Not sure never used kubuntu is it ksudo?, what ever the command is for super user.

---

