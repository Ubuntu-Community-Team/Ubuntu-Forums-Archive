---
title: "problems printing from a shared printer"
date: 2011-06-15
forum: General Help
---

### Post by hunterkasy on 2011-06-15
I have a hp business 1000 printer installed on a xubuntu 11.04 64 machine, I have the printer shared out. I am trying to print from a Ubuntu 11.04 64 unity machine, I can install the printer but I cannot authenticate to the xubuntu machine that has the printer installed when I try to print from the ubuntu machine it pops up with the authentication I put in the correct user-name and password and it does not go through I have tried many times and even went to the xubuntu machine to make sure I was putting in the right user-name and password. all is correct but still unable to print

I could use some help

thanks

---

### Post by pqwoerituytrueiwoq on 2011-06-15
open printing under system server -> settings [img]http://ubuntuforums.org/attachment.php?attachmentid=195203&stc=1&d=1308165452[/img]

---

### Post by hunterkasy on 2011-06-16
> **pqwoerituytrueiwoq said:**
> open printing under system server -> settings [img]http://ubuntuforums.org/attachment.php?attachmentid=195203&stc=1&d=1308165452[/img]

I already did that and it still wont let me print

---

### Post by Morbius1 on 2011-06-16
> I can install the printer but I cannot authenticate to the xubuntu  machine that has the printer installed when I try to print from the  ubuntu machine it pops up with the authentication I put in the correct  user-name and password and it does not go through I have tried many  times and even went to the xubuntu machine to make sure I was putting in  the right user-name and password.You shouldn't be prompted for a username and password at all unless you configured it that way in the Printing utility.  Are you using Samba by any chance? If you are you need to make a change to the samba config file to allow guest access. Or you need to create a samba user with it's own password.

---

### Post by hunterkasy on 2011-06-16
> **Morbius1 said:**
> You shouldn't be prompted for a username and password at all unless you configured it that way in the Printing utility.  Are you using Samba by any chance? If you are you need to make a change to the samba config file to allow guest access. Or you need to create a samba user with it's own password.

I am using samba "for a windows computer" I am guessing when it prompts for username and password is when my ubutnu machine is trying to "login" to my xubuntu machine

---

### Post by Morbius1 on 2011-06-17
Not sure I followed that but if you are using Samba on the Xubuntu machine to share the printer then you need to make the following correction to a config file so that you won't be prompted for a password:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find the section: [printers] and change it from this:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]**     guest ok = no**[/COLOR]
;    read only = yes
    create mask = 0700To this:
> [printers]
    comment = All Printers
    browseable = No
    path = /var/spool/samba
    printable = yes
[COLOR=Blue]**     guest ok = yes**[/COLOR]
;    read only = yes
    create mask = 0700Then save smb.conf, exit gedit and back in the terminal restart samba:
```
sudo service smbd restart
```

**EDIT:** Sorry, change "gedit" above to whatever editor you are using in Xubuntu.

---

### Post by hunterkasy on 2011-06-20
I had to make a samba user and that fixed the problem thanks for all of your help

---

