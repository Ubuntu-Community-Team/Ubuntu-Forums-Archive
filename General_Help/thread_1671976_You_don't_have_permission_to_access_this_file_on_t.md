---
title: "You don't have permission to access this file on this server."
date: 2011-01-20
forum: General Help
---

### Post by gujjerji on 2011-01-20
hello guys 
i was install ubuntu server with desktop 
and when i try to open my ip adress in browse it show me this 

**Forbidden**

 You don't have permission to access this file on this server.  Cheyenne/2.2.8 Server at localhost Port 80

how can i fix it please help me thank you 
you can check it 
My IP address is 88.163.109.209, you can see the directory forbidden error if you type in my IP address.

---

### Post by WorMzy on 2011-01-20
You mean you get something like this:
[[IMG]http://img684.imageshack.us/img684/9581/201101201950441001x883s.th.png[/IMG]](http://img684.imageshack.us/img684/9581/201101201950441001x883s.png)
?

That means that apache cannot read your file's content due to the apache user not having sufficient permissions on the file/folder in question.

Assuming that you've installed apache in the normal way, this command should work for you. If you've installed XAMPP or whatever to /opt, then modify the command to reflect that:
```
sudo chmod -R a+r /var/www
```

---

### Post by WorMzy on 2011-01-20
<double post>

---

### Post by gujjerji on 2011-01-20
> **WorMzy said:**
> You mean you get something like this:
[[IMG]http://img684.imageshack.us/img684/9581/201101201950441001x883s.th.png[/IMG]]("http://img684.imageshack.us/img684/9581/201101201950441001x883s.png")
?

That means that apache cannot read your file's content due to the apache user not having sufficient permissions on the file/folder in question.

Assuming that you've installed apache in the normal way, this command should work for you. If you've installed XAMPP or whatever to /opt, then modify the command to reflect that:
```
sudo chmod -R a+r /var/www
```

i got error some think like this

---

