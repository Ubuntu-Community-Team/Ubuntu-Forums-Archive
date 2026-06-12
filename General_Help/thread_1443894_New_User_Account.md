---
title: "New User Account"
date: 2010-03-31
forum: General Help
---

### Post by Aaron Durant on 2010-03-31
Hello,

I have accidentally screwed up my user account on ubuntu (im running 10.04 Alpha2 i think) and so i need to create a new user account. I have tried doing this in the Users and Groups utility but after i have created the account and set it as administrator, then try to log into it it says authentication failure. I have made sure i got the password exactly right but still have the same problem. I can set the account be logged in without a password but then cannot authenticate anything.

Please could someone tell me how i can fix this so that i can create a fully working administrator account and delete my old one.

Thanx

Aaron

---

### Post by 98cwitr on 2010-03-31
```
sudo su
useradd -m -s -g admin *username*
passwd *password*
```

Done!

---

### Post by Aaron Durant on 2010-04-01
Thanx

How am i meant to put this into terminal. Im not sure what sudo su does... and then i put in the useradd -m -s -g admin username it says that -g is an invalid shell. I have tried it with out the -g and it says -admin is an invalid shell...

---

