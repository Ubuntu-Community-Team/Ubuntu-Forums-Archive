---
title: "mysql error"
date: 2010-08-11
forum: General Help
---

### Post by rahulburra on 2010-08-11
hi 
when i run the below command in ubuntu 9.10
 	

 	 	 		 			 				 > mysql -u root -ppassword 			 		 	 	 
**the password of the root user in this case is 'password'**
i get output as below
 	

 	 	 		 			 				> ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES) 			 		 	 	 
please reply 
thankyou

---

### Post by rahulburra on 2010-08-11
please anyone help me with this error plese..
thankyou

---

### Post by Caskast on 2010-08-11
mysql -uroot -p

It will return Enter Password: 

If root dosnt have a password just do mysql -uroot

---

### Post by elricscripts on 2010-08-12
Solved in cross post:
[http://ubuntuforums.org/showthread.php?t=1550946](http://ubuntuforums.org/showthread.php?t=1550946)

---

