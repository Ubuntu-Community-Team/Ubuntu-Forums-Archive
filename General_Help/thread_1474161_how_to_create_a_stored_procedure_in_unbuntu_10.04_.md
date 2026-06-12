---
title: "how to create a stored procedure in unbuntu 10.04 mysql error 1307"
date: 2010-05-05
forum: General Help
---

### Post by _nate on 2010-05-05
recently upgraded, now none of my stored procedures work. All return error 1307.  what can I do to prevent this from happening?

---

### Post by utnubuuser on 2010-05-06
It's prbably the file permissions.  If your "prcedures" are executable scripts, check to make sure they've still got execute permissions.

---

### Post by _nate on 2010-05-06
I actually can't create them. It is saying I have an error on line 4 which is where 'CREATE PROCEDURE' is


DELIMITER $$

DROP PROCEDURE IF EXISTS `testing`.`test`$$
CREATE PROCEDURE `testing`.`test` ()
BEGIN

END$$

DELIMITER ;



Error while executing query: CREATE PROCEDURE `testing`.`test` ()
BEGIN

END:
Failed to CREATE PROCEDURE test (errno: 1307)
Click 'Ignore' if you'd like to have this error ignored until the end of the script.

---

### Post by _nate on 2010-05-07
In case anyone else has trouble here is what I did to resolve the problem:

cat /var/log/mysql/error.log

which yielded

column count of mysql.db is wrong. expected 22 found 20

which means that the database was corrupted.

To fix it I ran mysql_upgrade -u root -p

---

