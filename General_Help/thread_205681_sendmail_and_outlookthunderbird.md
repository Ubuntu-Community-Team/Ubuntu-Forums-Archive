---
title: "sendmail and outlook/thunderbird"
date: 2006-06-28
forum: General Help
---

### Post by syadnom on 2006-06-28
i have sendmail setup and am using the built in aliases to create forwarding groups via 

/etc/sendmail/aliases

and using includes in that file like

group1: :include:/opt/aliases/group1

and in /opt/aliases/group1 i have

user1
user2
user3

..

now, when using pine i can use these aliases just fine.  if i send a mail to [email]groop1@localdomain.net[/email], users 1,2, and 3 all get the email.  GREAT!

BUT!!!

if i use outlook or thunderbird, i cannot send to the aliases though i can send to the individual users.  in thunderbird, if i am user1, when i send a message to group1, i get an error

Subject: Returned mail: group1... aliasing/forwarding loop broken

but it works in pine!!

any ideas? am using thunderbird setup via pop3 btw.

---

### Post by syadnom on 2006-06-28
any ideas??

---

