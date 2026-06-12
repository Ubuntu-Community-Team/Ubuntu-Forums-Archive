---
title: "PHP , Prepared Statements, and mysqli driver"
date: 2012-01-13
forum: General Help
---

### Post by praxis1949 on 2012-01-13
Hi,

I am  running Ubuntu 11.01, mysql 5.1.58, and PHP Version 5.3.6. I am using the more advanced mysqli driver because it supports prepared statements, yet have been able to use prepared statements in "inserts" (to insert data via PHP into the mysql database). 

Anyone else having trouble using prepared statements with the mysql[COLOR="Red"]i[/COLOR] driver? Anyone found a quirk in the driver that caused enduring pain?

Regards

John S
Aylmer, Quebec

---

### Post by cj13579 on 2012-01-13
> **praxis1949 said:**
> Anyone else having trouble using prepared statements with the mysqli driver?

I haven't had any issues. What exactly are the type of problems you are hitting? Are you getting a particular error message back? Also, if you haven't done so already this is a good reference point: [http://php.net/manual/en/pdo.prepared-statements.php](http://php.net/manual/en/pdo.prepared-statements.php)

---

### Post by vectorthorn on 2012-07-24
it's likely because you're calling more than 1 sp from the same script connection, and not using the result sets properly, via mysqli_next_result();

---

