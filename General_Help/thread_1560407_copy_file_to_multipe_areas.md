---
title: "copy file to multipe areas"
date: 2010-08-24
forum: General Help
---

### Post by triunenature on 2010-08-24
Hey, i am trying to copy one file, to 5 locations...

I have an text file i want to place in all the users home

something like (i think this isn't it)

```
sudo cp readme.txt /home/user1 /home/user2 /home/user3
```



Any ideas?

(also, they need to be able to actually read the file, without permission denied errors)

Thanks in advance!!!

---

### Post by jobix on 2010-08-24
A small shell script might work.

> 
ls /home > /tmp/userlist

for i in `cat /tmp/userlist`
do
   sudo cp readme.txt /home/$i
done

rm /tmp/userlist


Haven't tested this.

Also, you might need to use a chmod at the end to ensure proper permissions.

---

### Post by Vaphell on 2010-08-24
or sudo chown $i:$i /home/$i/readme.txt to give it to the owners of home dirs

lost+found would obviously fail then as there is no such user, so **ls -I lost+found /home** would be better (-I = ignore pattern)

---

### Post by triunenature on 2010-08-24
[QUOTE=jobix]A small shell script might work.[QUOTE]

Haha!!! Good job! it worked.

Man i need to learn more about shell scripts...

Thanks a bunch.

---

