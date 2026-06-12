---
title: "login problem"
date: 2011-04-15
forum: General Help
---

### Post by roooqi on 2011-04-15
Hi everyone; I just bought this desktop from my friend and it runs win 7 and ubuntu 10.04. it worked very well the first two days until I changed the hostname of the system. 

I did like:
hostname myNewName

and everything worked fine. The problem now is when I start ubuntu and and reach username and password screen , I enter my password to login the screen becomes black and return me again to the screen where I put my password again. If I entered wrong password , the system message stating wrong password. On the other hand, when I try to run ubuntu from live-cd I can login easily and access my account. 
My friend told me he removed Naultius package and reinstall it for some reason before he gave it to me.
Note windows 7 is working properly.

Can any one help ?

Thanks and hope I explained well.

---

### Post by coffee412 on 2011-04-15
You changed your hostname. So, Take a look at the file /etc/hosts and make sure it reflects the change in your host name.

example:

> [coffee@coffee ~]$ cat /etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1    localhost.localdomain localhost
127.0.0.1    [www.xxxblackbook.com](www.xxxblackbook.com)
10.0.1.61    coffee.athome.net coffee


See if changing that to reflect your new hostname helps.


coffee

---

### Post by roooqi on 2011-04-15
the second line has the old one , how can I change it it is read-only file ?

Thanks again

---

### Post by Dutch70 on 2011-04-15
What do you mean it's read only? How did you try to change it?

I believe you need to use gedit to change it.
```
sudo gedit /etc/hosts
```
Change the name, then save it.

.

---

### Post by roooqi on 2011-04-15
I changed the name and saved it restart my pc , same problem 

Thanks

---

### Post by Dutch70 on 2011-04-15
Is it still showing the old name when you look in...
```
cat /etc/hosts
```

---

### Post by roooqi on 2011-04-15
now it is showing the new name.

how can I restore this file I mean backup the original file because I am afraid there is some thing wrong with 

If I got the original file back , I would edit it again

Thanks for help

---

