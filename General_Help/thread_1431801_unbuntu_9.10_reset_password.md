---
title: "unbuntu 9.10 reset password"
date: 2010-03-17
forum: General Help
---

### Post by sskrajak on 2010-03-17
Hi ubuntu gurus,
 
I have upgraded ubuntu from 9.04 to 9.10. While it was upgrading i changed my user password and now it is not identifying the old password or new password.
 
Also I am not able to reset the password through recovery mode. Since choosing any option from the displayed menu it is resulting in a prompt which is asking me to give the root password. I do not know my root password. I think reset passwrod mechanism is different in 9.10 then in its earlier version. since in earlier version no password was asked.
 
Please help me by telling me how i can reset the user password and the root password in ubuntu 9.10. It will be helpful if i know all the methods for this.
 
Regards
ssk

---

### Post by sikander3786 on 2010-03-17
Hi.

1. Enter the recovery mode when system starts.

2. Drop to root shell prompt.

3. Type

```

ls /home

```

That will show up the username (all the available home directories).

4. Type

```

passwd username

```
Where username is the name that you use to login.

5. You will be prompted to enter the new password. Enter it.

Hope that helps.

Sikander.

---

### Post by darolu on 2010-03-17
This _may_ help, boot using a LiveCD, mount your / partition, open a terminal and edit your shadow file:
```
$ sudo nano /etc/shadow
```
Find your user name, you'll see your password (encrypted), change the value to: **!** save the file and reboot.
This will tell the system that you account has no password and you should be able to log in without a password. Then you can restore your passwords following sikander's instructions.

---

### Post by sskrajak on 2010-03-17
selecting "Drop to root shell prompt"   ask for the root password which i do not know.
Anyway thanks for the reply. Please tell some other method if you know.

---

### Post by sskrajak on 2010-03-17
> **darolu said:**
> This _may_ help, boot using a LiveCD, mount your / partition, open a terminal and edit your shadow file:
```
$ sudo nano /etc/shadow
```
Find your user name, you'll see your password (encrypted), change the value to: **!** save the file and reboot.
This will tell the system that you account has no password and you should be able to log in without a password. Then you can restore your passwords following sikander's instructions.
 
"boot using a LiveCD" i do not have the cd. i updated through internet.

---

### Post by sskrajak on 2010-03-17
> **sskrajak said:**
> selecting "Drop to root shell prompt" ask for the root password which i do not know.
Anyway thanks for the reply. Please tell some other method if you know.
 
selecting "Drop to root shell prompt" ask for the root password which i do not know.
Anyway thanks for the reply. Please tell some other method if you know.

---

### Post by darolu on 2010-03-17
ANY LiveCD will do, use the one you used to install in the first place, or another distro's, you can use a pendrive also, you only need access to the /etc/shadow file and edit it.

---

### Post by sskrajak on 2010-03-17
> **darolu said:**
> ANY LiveCD will do, use the one you used to install in the first place, or another distro's, you can use a pendrive also, you only need access to the /etc/shadow file and edit it.
Thanks. This will help i think.

---

### Post by sikander3786 on 2010-03-17
> **sskrajak said:**
> selecting "Drop to root shell prompt" ask for the root password which i do not know.
Anyway thanks for the reply. Please tell some other method if you know.

Well on my machine Ubuntu drops to root shell prompt without asking the password.

Here is an other way to reset the password.

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

Hope it helps this time.

---

