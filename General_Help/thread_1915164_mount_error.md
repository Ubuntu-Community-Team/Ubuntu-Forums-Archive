---
title: "mount error"
date: 2012-01-25
forum: General Help
---

### Post by rsumon on 2012-01-25
HI,
 I have a Dell latitude laptop. I have installed Ubuntu 11.04. I was trying to mount my windows server 2003 server share folder to my Ubuntu laptop. Here is my fstab entry:

//192.168.1.101/Fileserver/MediaArchiv    /media/fileserver smbfs  
username=rsumon,password=nomusr,uid=demo,gid=demo 0 0  

I was able to mount with it after running "sudo mountall" from my terminal i can see it there but Now I am getting an error when I am shutting down the computer in the screen it gives the message below and freeze for long time may be min or more.  

mountall: mount /home/user/Fileserver [5122] terminated with status 255 error 1 (unknown error 4294967295) opening credintial file /root/.smbcrediantials.
After waiting some times it shut down the computer. I have the same command in my desktop there is no error. 

Please help.

Thank you

---

### Post by mörgæs on 2012-01-26
Moved to General Help as this is not a specific Dell problem.

---

