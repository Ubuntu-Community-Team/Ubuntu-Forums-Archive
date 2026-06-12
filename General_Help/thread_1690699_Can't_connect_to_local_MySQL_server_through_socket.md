---
title: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2011-02-18
forum: General Help
---

### Post by Nixxous on 2011-02-18
Hi im trying to setup mysql for my ubuntu server 10.10 but i keep getting error
```
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```so i tried **start mysql** and got this error:
```
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=3591 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

```i have reinstalled both mysql-client and mysql-server and tried again but i still get the same errors, i have tried many different solutions that i have found by googling, and i either still get the errors or i get the same errors during trying the solution.

help would be much appreciated, thanks

---

### Post by Nixxous on 2011-02-19
ok i found my problem, it was in the my.cnf, in the guide i was using it told me to comment out the line with bind address on it, that was supposed to make it so others could connect over the internet, being a new linux and a new mysql user i followed the guide right down to every command......

i then saw a guide about fixing the problem, and that said to change my bind address to my ip address, so i changed it to the ip that others use to connect to my computer, i still came up with the same error, so i changed it back to 127.0.0.1 and it works again.

so my question now is, will having bind address set as 127.0.0.1 still allow others to connect to my computer over the internet?:confused:

---

### Post by Habitual on 2011-02-19
bind address=(IP of the system)

bind_address=127.0.0.1 would ONLY allow the local host to connect because the listener only "hears" localhost.

When others connect (bind_address=ipa.ddr.ess) then "mysql **-h **ipa.ddr.ess -u $user -p $password" would have to be used.

---

### Post by Nixxous on 2011-02-19
ok thanks alot! so once i need others to connect i just do
```
mysql **-h **ipa.ddr.ess -u $user -p $password
```and type in my external IP instead of where it says ipa.ddr.ess and others should be able to connect?

---

### Post by Habitual on 2011-02-19
Yes sir, that should do it.

---

### Post by Nixxous on 2011-02-19
GREAT!!! thanks so much!!!

---

### Post by Habitual on 2011-02-19
Not a problem!

---

### Post by Nixxous on 2011-02-19
ok when i type it in the command line, it just sits there and doesnt do anything for ages.
so i dunno whats wrong there.
is there any way to do it without having to type that into the console everytime?

---

### Post by Habitual on 2011-02-19
did you restart mysql after changing the port?

What happens after "ages"?

---

### Post by Nixxous on 2011-02-22
well iv got a new server now, so once it gets to that part again, probly later on, i'll let you know

---

### Post by asmoore82 on 2011-02-22
> **Nixxous said:**
> ok i found my problem, it was in the my.cnf, in the guide i was using it told me to comment out the line with bind address on it,**that was supposed to make it so others could connect over the internet**, being a new linux and a new mysql user i followed the guide right down to every command.....
There are massive security implications of opening your database server
to the outside world. Typically, a database is only exposed to some middleware
or "application server" and this server handles business with the outside world.

---

