---
title: "Administration question"
date: 2010-02-06
forum: General Help
---

### Post by Barashkukor on 2010-02-06
If I were to do this when I had only one user account;

System>Administration>User and Groups.

Unlocked the settengs.

Go to Properties then User Privileges tab.

Uncheck administer the system.

Set new sudo password.

Closed to apply changes.

Would I not be able to use sudo from that account?  I ask because either I entered the sudo password wrong twice when setting it, or I cant sudo from the command line in an account without the ability to administrate.  

I don't know what to do now since I need to be able to administer the system, and the best I can think of is reformatting.

---

### Post by sisco311 on 2010-02-06
Boot in the *Recovery Mode* and add your user to the admin group:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Barashkukor on 2010-02-06
Thank you very much, solved my problem!  Some people were trying to tell me how to do this last week but they never mentioned that I had to enter recovery mode in order to get the root shell, so I was stuck.  Thanks again for your help!

---

