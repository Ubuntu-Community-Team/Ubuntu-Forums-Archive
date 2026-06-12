---
title: "Says there are updates but there ate not at tty login"
date: 2011-06-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-15
when i login to my sisters computer to run updates/shut it off when she leaves it running over ssh i get this
```
Linux maggie-desktop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

6 packages can be updated.
3 updates are security updates.

Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

20 packages can be updated.
12 updates are security updates.

Last login: Sun Jun 12 14:09:59 2011 from linux-desktop.local
```it appears to be displaying the login text 2 times but only the 1st one it accurate
i am wondering why it is doing that

---

### Post by Toz on 2011-06-15
In a nutshell, when you login, **/etc/pam.d/login** is run. A command in that file **session    optional   pam_motd.so**, executes all the scripts in /etc/update-motd.d. The **90-updates-available** file creates one of the "updates available" outputs. Also, **99-footer** runs any administrator-specific messages including catting the file **/etc/motd.tail**.

I would first look at all the files in **/etc/update-motd.d** to see if there is a duplicate set of commands to create the update output.

I would also look to see if an **/etc/motd.tail** file exists. On my install of 11.04, I do not have this file. If it exists on your sister's computer, you can try renaming the file to see if it is the culprit.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
thanks 
[FONT=Courier New]sudo rm /etc/motd.tail[/FONT]
fixed it

---

