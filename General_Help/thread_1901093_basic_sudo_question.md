---
title: "basic sudo question"
date: 2011-12-27
forum: General Help
---

### Post by Bastun on 2011-12-27
Hi I have just installed 10.04 and want to install Skype. Requests I enter command initially:
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"

....but then asks for a password!!!!!! I dont know any password except my login,,which does'nt work.

Sorry to be such a muppet but any help on this would be great.


Regards,

Bastun

---

### Post by whatthefunk on 2011-12-27
How many accounts do you have set up on your pc?  Unless youve messed around with usergroups and user privileges, the account that you initially set up on the computer when you installed the OS should be the root user and that password should work for sudo.

---

### Post by linuxman94 on 2011-12-27
Your password will work, but it will not show anything on the screen when you enter it.  This a security feature to prevent people from looking over your shoulder and seeing the length of your password.  Just type it in and hit enter.

---

### Post by overdrank on 2011-12-27
moved to General Help

---

### Post by Bucky Ball on 2011-12-27
Isn't it available in Synaptic Package Manager already?

---

### Post by whatthefunk on 2011-12-27
> **Bucky Ball said:**
> Isn't it available in Synaptic Package Manager already?

Youd still need your password to install it.

---

### Post by Bucky Ball on 2011-12-27
> **whatthefunk said:**
> Youd still need your password to install it.

Sure, so perhaps the password rejection is the real issue here ... ;)

---

### Post by lisati on 2011-12-27
> **Bucky Ball said:**
> Sure, so perhaps the password rejection is the real issue here ... ;)

Sometimes the hiding of the sudo password in the terminal confuses new users, and it looks like it's not working when it really is. See post 3.

---

### Post by Bastun on 2011-12-28
thanks for your time folks...all clear now :)

---

