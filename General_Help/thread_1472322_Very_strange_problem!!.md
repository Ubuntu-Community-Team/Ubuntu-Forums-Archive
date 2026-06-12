---
title: "Very strange problem!!"
date: 2010-05-04
forum: General Help
---

### Post by ibrahim.k on 2010-05-04
Hi,

After installing 10.04 and loged in to my system for the first time. using the username and password.
I wanted to setup  the chat accounts but the system was asking me about

Enter the password for keyring "Default" 


I have entered the same password I log in with !!! but he is telling me that password is incorrect.

I have changed the password but still not working

---

### Post by dino99 on 2010-05-04
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

maybe you know also how to use google

---

### Post by doas777 on 2010-05-04
go to 
Accessories -> Passwords and encryption keys, and select the key called 'Default'.
then right click and select "Change password". 

ubuntu tries to store all your saved passwords securely (by encrypting them) but needs a password to access them. this is your keyring or unlock password ('Default'). 

my recomendation is that you set your default password to be the same as the one you use to login to your desktop. that way your keyring is automatically unlocked at login.
if you auto login however, this will not work quite right, and you will be prompted for the default password. 

here one user provided an interesting fix. instead of setting the two passwords to match he/she is setting the login password to be used as the 'Default'.
[http://ubuntuforums.org/showpost.php?p=9217454&postcount=3](http://ubuntuforums.org/showpost.php?p=9217454&postcount=3)


hth

---

### Post by doas777 on 2010-05-04
> **dino99 said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

maybe you know also how to use google

um, neither of those have anything to do with the keyring password.
maybe you know also how to read.

---

### Post by ibrahim.k on 2010-05-04
> **doas777 said:**
> go to 
Accessories -> Passwords and encryption keys, and select the key called 'Default'.
then right click and select "Change password". 

ubuntu tries to store all your saved passwords securely (by encrypting them) but needs a password to access them. this is your keyring or unlock password ('Default'). 

my recomendation is that you set your default password to be the same as the one you use to login to your desktop. that way your keyring is automatically unlocked at login.
if you auto login however, this will not work quite right, and you will be prompted for the default password. 

here one user provided an interesting fix. instead of setting the two passwords to match he/she is setting the login password to be used as the 'Default'.
[http://ubuntuforums.org/showpost.php?p=9217454&postcount=3](http://ubuntuforums.org/showpost.php?p=9217454&postcount=3)


hth



Thank you veryyy much the problem has been solved :)

---

