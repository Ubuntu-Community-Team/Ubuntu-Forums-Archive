---
title: "can't create new account..."
date: 2005-03-07
forum: General Help
---

### Post by Gerry on 2005-03-07
I can't create a new account at shipit. Whenever I fill out the form and submit it, I get to an error page which says
 ```
Traceback (most recent call last):
  File "user.cgi", line 138, in ?
    main()
  File "user.cgi", line 80, in main
    page.new( new_values )
  File "./lib/shipit.py", line 358, in new
    db.insert_new_user( new_values )
  File "./lib/db.py", line 396, in insert_new_user
    db.execute( sql, valuedict )
  File "./lib/db.py", line 39, in execute
    cursor.execute( statement, valuedict )
IntegrityError: ERROR:  duplicate key violates unique constraint "recipient_pkey"

INSERT INTO Recipient ( province, city, givenname, quantitydesired, address1, address2, familyname, quantitydesiredppc, announcements, phone, postcode, country, passwordhint, organization, password, quality, email, quantitydesiredamd64 ) VALUES ( NULL, 'xxxxxxx', 'xxxxx', '10', 'xxxxxxxxxx', NULL, 'xxxxxx', '0', 0, 'xxxxxxxxxxx', 'xxxxxx', 'XX', NULL, NULL, 'xxxxxx', 7, 'xxxxxxx', '0' )
```
and I have no account. Is it my fault and if yes, what shall I do? I already tried with Mozilla, Firefox, Konqueror and IE.

---

### Post by kassetra on 2005-03-07
Hi!  You need to email [email]mako@canonical.com[/email]
[http://www.ubuntulinux.org/support/documentation/faq/shipit/](http://www.ubuntulinux.org/support/documentation/faq/shipit/)

---

### Post by Gerry on 2005-03-08
Thank you... I just thought perhaps someone else here would have had this error too and found a solution to this, being able to share it with me. 
Can anyone try to create a new account to see if he/she gets an error? Just to know that it's not only me...

---

### Post by mario001 on 2005-03-08
hello,

i've got same error msg.

hmmm...  :cry:

---

