---
title: "Remove lock icon from read-only files"
date: 2011-09-23
forum: General Help
---

### Post by stanix on 2011-09-23
Hello community,

Does anybody know how one can get rid of this lock icon which is attached to a file icon if the file is set to read-only without changing the file permissions? Maybe there is a setting in Nautilus or one can simply replace this lock icon somewhere in the system by an empty icon so you effectively do see nothing (where is it located?)?

Background: I usually set my photos to read only and my view zoom in Nautilus is set to 33%. with this setting the lock icon covers almost the whole file icon which I find quiet annoying.

Thank you for your help,
Stan

---

### Post by raja.genupula on 2011-09-23
Hi 
     Look at the file properties from there you can do it , i mean changing that symbol . i think it is a Emblem . so you can do it by changing emblem of it . 
one more thing is you can modify the read only file permissions by making as 
 
```
sudo chmod 700 filename
```
by using this you (user who is a root on multi user & user it self on a single user ) can change the file permissions read ,write & execute for the current user ..

But dont touch system files . 
all the best .

---

