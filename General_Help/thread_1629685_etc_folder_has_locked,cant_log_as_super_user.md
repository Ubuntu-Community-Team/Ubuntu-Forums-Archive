---
title: "etc folder has locked,cant log as super user"
date: 2010-11-24
forum: General Help
---

### Post by ishk on 2010-11-24
hi
i gave the permission (chmod 647) to etc folder without thinking much. and now i cant
log as root and cant do anything. i want to remove this permission plz help me to solve this
br

---

### Post by blazemore on 2010-11-24
If you recursively set the permissions (ie set the permissions on /etc/ and all files under it) there's not really much you can do short of reinstalling and not doing it again.

---

### Post by ishk on 2010-11-24
thanks :( :(

---

### Post by dcstar on 2010-11-24
> **ishk said:**
> hi
i gave the permission (chmod 647) to etc folder** without thinking much**
.........

Yes, that is an accurate statement.

Don't stuff around with your system in any way, things are the way they are for a reason.

---

### Post by iponeverything on 2010-11-24
> **ishk said:**
> hi
i gave the permission (chmod 647) to etc folder without thinking much. and now i cant
log as root and cant do anything. i want to remove this permission plz help me to solve this
br

boot up with the live disk, mount the drive rw and change it back to 755.

---

### Post by ishk on 2010-11-24
thanks for all your replies,i just reinstalled it.but i think it is better to provide some warnings from ubuntu when 
newbie try to run such stupid commands

---

### Post by James78 on 2010-11-24
> **ishk said:**
> thanks for all your replies,i just reinstalled it.but i think it is better to provide some warnings from ubuntu when 
newbie try to run such stupid commands
Rather, I think they should have a special type of permissions file that tells what the permissions of system directories and system files are. Then just add a a special command, that one can use to reset the permissions with.

---

