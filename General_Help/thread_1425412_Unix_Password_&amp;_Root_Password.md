---
title: "Unix Password &amp; Root Password"
date: 2010-03-09
forum: General Help
---

### Post by Richiegs on 2010-03-09
1. I tried to change my password by typing "passwd" in the terminal. It then asked me to input the Unix password. After I typed in the Unix password, it read "Authentication token manipulation error". Why did that happen? I know what the Unix password is.

2. . What is the difference between Unix password and Root password?

Thanks

---

### Post by richardjh on 2010-03-09
The **UNIX password** it is asking for is **your password**. 
Assuming that you aren't doing anything not mentioned here, like running it as root.

You need to enter your password to continue, then it asks what you want the new password to be and then confirm it.

The **root password** is the **password of the root user**, which on Ubuntu is meaningless (by default) as the root account is not enabled. You have to access it via sudo.

---

### Post by Richiegs on 2010-03-09
> **richardjh said:**
> The **UNIX password** it is asking for is **your password**. 
Assuming that you aren't doing anything not mentioned here, like running it as root.

You need to enter your password to continue, then it asks what you want the new password to be and then confirm it.

The **root password** is the **password of the root user**, which on Ubuntu is meaningless (by default) as the root account is not enabled. You have to access it via sudo.

Thank you

---

