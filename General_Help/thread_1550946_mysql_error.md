---
title: "mysql error"
date: 2010-08-11
forum: General Help
---

### Post by rahulburra on 2010-08-11
hi 
when i run the following command in my ubuntu 9.10
> mysqladmin -u root password 'password'
i get the following error
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
its not even asking me the password im getting the error directly
can anyone please help me solve the problem
thankyou

---

### Post by DaithiF on 2010-08-11
```
mysqladmin -u root -ppassword
```
(replace password with your actual root password of course, and no space between the -p and the password).

---

### Post by rahulburra on 2010-08-11
thanks a ton for the reply.....:p

---

### Post by rahulburra on 2010-08-11
hi 
when i run the below command in ubuntu 9.10
>  mysql -u root -ppassword
**the password of the root user in this case is 'password'**
i get output as below
> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
please reply 
thankyou

---

