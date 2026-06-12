---
title: "setting up ftp server"
date: 2005-03-03
forum: General Help
---

### Post by lightyear on 2005-03-03
Hi everyon,

I installed linux ubuntu on my pc....is my first experience with linux.  (looks good by the way) I thought ubuntu had a ftp server installed by default, but can't find it. During the installation there was some update that i skipped because i read somewhere that this was giving mayor hassels. I am not sure if this caused the server not to be installed, and if so where can i download it from to reinstall it.

Or ar there any tips on what ftp server to install.

Bas

---

### Post by Jad on 2005-03-03
**Pure-ftpd**
*Advantages*:
 Faster Login Time
 Smaller Memory Footprint
 Allows Virtual Access on any ip address
 Better Security Model
 Virtual User Quotas
 Deals better with Software Raid systems
 can use LDAP or MySQL user authentications
*Disadvantages*
There is no module for it with webmin 

**ProFTP**
*Advantages*
 can use LDAP ,MySQL, PostgreSQL user authentications
 There is a webmin module for it

Disadvantages
 Larger Memory Footprint

now how to install it 
go to 
Computer -> System configuration -> Synaptic Package Manager
Now if you want to install Pure-ftp search for pure-ftp and mark the needed packages for installations 
same if you want to install proftp 

Good luck 
happy FTPING!

---

### Post by lightyear on 2005-03-03
Hi Jad,

Thanks for your reply.  I don't find the ftp servers in this list. Where does the synaptic package manager it gets it info from...from the internet. I reloaded the list but no luck. Or must i download the package seperate?

Thanks Bas

---

### Post by HungSquirrel on 2005-03-03
You need to [enable the universe repository](http://ubuntuforums.org/showthread.php?t=179&highlight=universe) for those ftp daemons to show up.

Let me throw in a recommendation for vsftpd.  Lots of features, a great security reputation, and available in the normal repositories.

---

### Post by Jad on 2005-03-03
lightyear, 
enable universe repositories
give a time to read UbuntuGuide its damn usefull man 
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by lightyear on 2005-03-03
Thanks worked all fine...had 2 get used to the way linux works (still a lot to learn!)

---

### Post by Jad on 2005-03-03
congrats

---

### Post by pigpen on 2005-03-04
Glad I found this thread. I also have pure-ftpd server, but can anyone tell me how to stop the service? I browsed the pure-ftpd faq and I learned stuff on how to setup users and such but not much on how to actually stop pure-ftpd.  I assume there are two ways of stopping it, depending on if you started pure-ftpd as a inetd or standalone service.  I'd like to know both ways. I tried 'killall pure-ftpd' but it didn't work (as root).

Thanks in advance.

---

