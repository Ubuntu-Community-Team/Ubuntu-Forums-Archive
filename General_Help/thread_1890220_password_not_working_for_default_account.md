---
title: "password not working for default account"
date: 2011-12-03
forum: General Help
---

### Post by T_1000 on 2011-12-03
Hi,
I have ubuntu 11.10 64 bit. Today, I added some users from my default admin account. Also i set password to None for admin account just in case to avoid login pop up window at each installation. 

But since then I am not able to install anything. It says, unsuccessful login whenever I provide password or no password to my default account. Also I cannot change the setting since I cannot unlock from user account setting as even there it says invalid login credentials. 

Please assist.

Regards,

T_1000

---

### Post by bluexrider on 2011-12-03
This will probably get you there
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by T_1000 on 2011-12-03
> **bluexrider said:**
> This will probably get you there
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I tried the guideline but after entering new password it gives error "Authentication token manipulations error"

please advise

---

### Post by snlzkn on 2011-12-03
I received the same error but then I found out that first you have to select the option that mounts the system as read write. After that you should drop to shell prompt. When I did that I was able to change the password.

---

### Post by jaimeaux on 2011-12-03
Also, if you don't want to go with the above provided guide, you can just modify your kernel arguments (by using the listed options below), and add "single" to the end, and then boot. You'll then boot to a terminal where you're logged in as root. Then you just need to type 'passwd' as listed in the guide, and you'll be able to change it. 
 
This should also bypass the error you've been receiving. 
 
Hope this helps!

---

