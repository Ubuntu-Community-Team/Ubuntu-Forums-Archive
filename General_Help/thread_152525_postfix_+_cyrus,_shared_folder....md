---
title: "postfix + cyrus, shared folder..."
date: 2006-03-30
forum: General Help
---

### Post by paca on 2006-03-30
Hi, 
I have configured postfix to deliver to cyrus, and it works perfect for mailboxes.. but not shared folder.
I have a shared folder called admin, and postfix says
*data format error. Command output: admin: Mailbox does not exist*

in main.cf:
mailbox_transport = cyrus

and master.cf:
cyrus   unix    -       n       n       -       -       pipe    flags=R user=cyrus      argv=/usr/sbin/cyrdeliver -e -m ${extension} ${user}

any ideas?

Thanks in advance
/Paca

---

### Post by paca on 2006-03-30
I just figered out that ${extension} in master.cf tags it with **user.**, that's why only mailboxes in cyrus that is created with cm user.<user> works... and my shared is created with cm <shared> doesnt work...

/Paca

---

