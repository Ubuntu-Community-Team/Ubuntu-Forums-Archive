---
title: "Mysql Errors Can't Logon as Root"
date: 2010-01-11
forum: General Help
---

### Post by indigoseth on 2010-01-11
Hi All, 

I went away this weekend and everything with my mysql server was working great.  I got home on sunday, and I found that my web pages couldn't be displayed because they were unable to gain access to the mysql database.

I am now not able to log into mysql using root or debian-sys-maint. I get error messages.

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


I have tried loading mysql in safe mode, and changing the passwords, but this does little to help me.

I am unable to retart my services without them failing, so after making the changes i have to manually kill the processes for mysql to get it to stop.

After doing that i try to start mysql up, and it gives me a .sock error.

I will post some of the errors in my next post, but if anyone has a general idea what i can try to manually override the passwords or reset them it would be apprecated.

I did read that i can reset the debian-sys-maint password using the msql/rm.conf , but i am unable to log on as root to change the password :(

---

### Post by indigoseth on 2010-01-12
does anyone have some feed back on this.  Please?

---

### Post by wojox on 2010-01-12
It appears your root account has been disabled. You entered:

```
mysql -u root -p <enter>
```

Did you not set up a Admin account and grant all privileges to?

---

