---
title: "Root password"
date: 2011-10-28
forum: General Help
---

### Post by Eugezilla on 2011-10-28
I am attempting to install drivers for a Lexmark printer on my Ubuntu 11.10 computer but it keeps asking me for the Root (Administrator) password.  

I did not set up a root password when installing Ubuntu and have only one user account.  I have tried the password for the on account and it is rejected.  I have also tried every standard password I may have used and many of the standard passwords (like Root or Password). 

Any ideas?

Thanks in advance for your assistance.

---

### Post by haqking on 2011-10-28
> **Eugezilla said:**
> I am attempting to install drivers for a Lexmark printer on my Ubuntu 11.10 computer but it keeps asking me for the Root (Administrator) password.  

I did not set up a root password when installing Ubuntu and have only one user account.  I have tried the password for the on account and it is rejected.  I have also tried every standard password I may have used and many of the standard passwords (like Root or Password). 

Any ideas?

Thanks in advance for your assistance.

how are you installing the drivers ?

it is likely you need to use sudo, read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

what model is it ? as i know there are some issues with some lexmark, see here [http://ubuntuforums.org/archive/index.php/t-1243920.html](http://ubuntuforums.org/archive/index.php/t-1243920.html)

---

### Post by tom.swartz07 on 2011-10-28
> **Eugezilla said:**
> I am attempting to install drivers for a Lexmark printer on my Ubuntu 11.10 computer but it keeps asking me for the Root (Administrator) password.  

I did not set up a root password when installing Ubuntu and have only one user account.  I have tried the password for the on account and it is rejected.  I have also tried every standard password I may have used and many of the standard passwords (like Root or Password). 

Any ideas?

Thanks in advance for your assistance.

The Root password is invoked when you run the command with sudo - 99% of the time, your root password is the same as the primary user login, unless you explicitly changed it.

---

### Post by haqking on 2011-10-28
> **tom.swartz07 said:**
> The Root password is invoked when you run the command with sudo - 99% of the time, your root password is the same as the primary user login, unless you explicitly changed it.

that is not technically true.  There is no ROOT password as the ROOT account is locked by default, the only time there is a ROOT password in Ubuntu if the ROOT account has been unlocked by setting one.  Admin privelege on the other hand is obtained by using SUDO if in the SUDO group and you authenticate to SUDO by using your OWN user password if as i said you are in the SUDO group, SUDO and ROOT password are not the same thing

---

### Post by lisati on 2011-10-28
Please see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

