---
title: "Where is my 420GB disk???"
date: 2011-03-14
forum: General Help
---

### Post by bornon720 on 2011-03-14
I have 500 GB for total

50GB   mount point /       [ext4]
7 GB   ............/root   [ext4]
420GB  ............/home   [ext4]

After my installation(I didnt click encrypt home while I am filling who I am). 

Now.. I click place   computer

I can only see 
 CD/DVD Drive 
 Generic-Multi-Card
 File system (Properties..the Size is 50GB)

Where is my 420GB???

Thank you

---

### Post by kiyop on 2011-03-14
Click "Places"->"Home".

You made 420GB partition mounted on /home.

Please look /etc/fstab.

$ more /etc/fstab

---

