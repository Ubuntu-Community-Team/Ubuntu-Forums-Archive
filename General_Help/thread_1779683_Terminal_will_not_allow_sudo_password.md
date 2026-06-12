---
title: "Terminal will not allow sudo password"
date: 2011-06-10
forum: General Help
---

### Post by oliver474 on 2011-06-10
I know that it doesn't show up for security reasons. However, when I hit enter, the message "Sorry, try again" comes up.

I've entered the password correctly, I know this, (because I've typed it very slowly and carefully to be sure) but this error will not stop appearing. I've not been able to do **anything** in the terminal because of this, and what I'm trying to do **is a necessity** and cannot be done any other way. (Software index broken, the system crashed in the middle of a software upgrade, and a few programs are completely unusable.) 

Can anyone help? I'm pretty desperate at this point. 

Pictures are included, if I uploaded them correctly. New to forum, hello. 

Thanks. 

-Oliver

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **oliver474 said:**
> I know that it doesn't show up for security reasons. However, when I hit enter, the message "Sorry, try again" comes up.

I've entered the password correctly, I know this, (because I've typed it very slowly and carefully to be sure) but this error will not stop appearing. I've not been able to do **anything** in the terminal because of this, and what I'm trying to do **is a necessity** and cannot be done any other way. (Software index broken, the system crashed in the middle of a software upgrade, and a few programs are completely unusable.) 

Can anyone help? I'm pretty desperate at this point. 

Pictures are included, if I uploaded them correctly. New to forum, hello. 

Thanks. 

-Oliver

change your password..

In your terminal enter:

sudo passwd USERNAME

Reboot your system.. 

Then try it again.

---

### Post by oliver474 on 2011-06-10
Hmmm. I tried that, and this appeared:

oliver@ubuntu:~$ sudo passwd oliver
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
oliver@ubuntu:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
oliver@ubuntu:~$ sudo dpkg --configure -a
dpkg: error: parsing file '/var/lib/dpkg/updates/0048' near line 0:
 field name `
oliver@ubuntu:~$

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **oliver474 said:**
> Hmmm. I tried that, and this appeared:

oliver@ubuntu:~$ sudo passwd oliver
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
oliver@ubuntu:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
oliver@ubuntu:~$ sudo dpkg --configure -a
dpkg: error: parsing file '/var/lib/dpkg/updates/0048' near line 0:
 field name `
oliver@ubuntu:~$

Try this in your terminal:

     sudo rm /var/lib/apt/lists/* -vf 
 
     sudo apt-get update 
 
     sudo dpkg --configure -a

---

### Post by oliver474 on 2011-06-10
Thank you! This seems to have fixed the problem, and I am going to try reinstalling the programs that were not working.

---

### Post by linuxinstalledfromhdd on 2011-06-10
here is a nice guide to 11.04 and 10.10 too:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

