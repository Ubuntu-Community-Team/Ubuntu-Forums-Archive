---
title: "Help me with mysql recovery or Server recovery"
date: 2010-11-09
forum: General Help
---

### Post by gmakhs on 2010-11-09
hi today my server crashed and it loads on busybox i don't know how can i repair this so i thinked to format the server and start all over but i have a question there is any way to restore ther mysql files??? they haven't deletes there should be saved somewhere

---

### Post by kanishkdudeja on 2010-11-09
it the os starting ? or it doesnt even start ?

---

### Post by Hippytaff on 2010-11-09
If your getting dropped into busybox you might be able to startup in recovery mode by selecting it at boot (F1 I think should give you the boot options). Then you should be able to backup your data onto an extenal drive (usb, dvd) and then either try fixing the install or reinstall ubuntu server.

---

### Post by gmakhs on 2010-11-09
the Os doesn't run i use ubuntu server 10.10 on a dedicated machine so i can't change the boot option i have manage to resque my home folder files thoh  a resque system but what about mysql?

---

### Post by Hippytaff on 2010-11-09
I'm not porficient in this, but I read that you can try to
> 
copy /var/lib/mysql/mydata/ to external media

Though, how you access that I'm not sure...might you be able to boot from liveCd ot USB, and get access to the data that way?

---

### Post by gmakhs on 2010-11-09
using a resque OS i can acces the hard disk with terminal and im able to bopy data from it

---

### Post by Hippytaff on 2010-11-09
Excellent - are you sorted?
 
If your happy that you're problem is solved remember to mark the thread as solved in the thread tools at the top of the page so others who encounter the same issue can benefit from what you did :-)

---

### Post by gmakhs on 2010-11-09
until now i hgave manage to backup my files but what about mysql?? how can i buckup it??

---

### Post by SeijiSensei on 2010-11-09
Read up on [mysqldump]("http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html").  It creates a plain-text file from your database that you can use to restore it if necessary.

I have been able to copy the contents of /var/lib/mysql to a new machine and get MySQL to work with it.  I could even use a v4 database with MySQL 5.  That said, I much prefer mysqldump (and pg_dump for PostgreSQL) to avoid problems with binary incompatibilities.

---

### Post by gmakhs on 2010-11-09
thats a nicxe backup command but my mysql istn't working becouse server crashed :)

---

### Post by gmakhs on 2010-11-09
so any help on hopw can i find my database from the old hard disk witht he broken os?

---

### Post by gmakhs on 2010-11-09
after a lot of work i manage to save my database!!!!

you have to go at 
/var/lib/ and copy  the mysql folder
after the new O/S instalization tou put this folder back to 
/var/lib/
and after you install the mysql and databases will work :D

---

### Post by Hippytaff on 2010-11-09
Excellent :-)

Remember to mark the thread as solved in the thread tools at the top of the page so others can benefit from your hard work :-)

---

### Post by gmakhs on 2010-11-10
done thanks for the help!

---

### Post by Hippytaff on 2010-11-10
> **gmakhs said:**
> done thanks for the help!

I didn't really help much to be honest :-)

glad its sorted though

---

