---
title: "I forgot root password in ubuntu 11.10"
date: 2012-03-09
forum: General Help
---

### Post by ubun2os on 2012-03-09
i googled very much. i saw [http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html](http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html)

and i tested editing /etc/shadow file and deleted between first : and second :. but didn't work correctly.

i use ubuntu 11.10. how do I gather or reset root password?

---

### Post by idoitprone on 2012-03-09
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

type
> passwd username[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

root is diable on default on ubuntu

---

### Post by ubun2os on 2012-03-19
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)[IMG]http://www.psychocats.net/ubuntu/images/resetpasswordoneiricthumb01.jpg[/IMG]
i could not enter to recovery menu. i select recovery mode but i can't see recovery mode.!!!!

---

### Post by raja.genupula on 2012-03-19
[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

then use this to reset , how system behaving when you click at Recovery mode in Grub  ?

---

### Post by chubbtech on 2012-03-31
If you have admin rights, just sudo passwd root, enter your admin password then change the root password

---

### Post by idoitprone on 2012-04-01
> **chubbtech said:**
> If you have admin rights, just sudo passwd root, enter your admin password then change the root password


this is ubuntu, he should not change root but the user that has admin rights

---

### Post by raja.genupula on 2012-04-01
> **idoitprone said:**
> this is ubuntu, he should not change root but the user that has admin rights

yup +1 , root account is with the admin username .

---

