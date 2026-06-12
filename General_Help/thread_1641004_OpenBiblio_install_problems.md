---
title: "OpenBiblio install problems"
date: 2010-12-08
forum: General Help
---

### Post by new2linux09 on 2010-12-08
Hello all,

I'm attempting to install OpenBiblio to give it a test drive. I'm having trouble with one of the first steps within the openbiblio install guide. The step is dealing with MySQL in creating user priveleges to the db created. The step is:

Create an OpenBiblio database user. To do this, login to MySQL under the admin userid and run the following SQL command, substituting obiblio_user and obiblio_password with the userid and password of your choice.

    mysql> grant all privileges on OpenBiblio.* to obiblio_user@localhost
        -> identified by 'obiblio_password';

When I run the "grant all priveleges" command I receive a syntax error. 
I've spent some time googleing and it comes up with the same command. There has been a few variations attempted such as 'obiblio_user'@'localhost' but still recieve a syntax error. 

Anyone have ideas on how to move past this step and move forward with the installation?

---

### Post by new2linux09 on 2010-12-09
Anyone have an idea? Or perhaps another suggestion for library software? I've been experimenting with Koha but its very technical and would like something a little more simplified.

---

### Post by jinglada on 2011-07-22
Have you tryed this way:
mysql> grant all privileges on OpenBiblio.* to obiblio_user@localhost identified by 'obiblio_password';

That is, all in one line?

---

