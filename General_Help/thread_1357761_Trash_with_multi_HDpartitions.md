---
title: "Trash with multi HD/partitions"
date: 2009-12-17
forum: General Help
---

### Post by bhsu17 on 2009-12-17
Hi peoples,

'lil help here please.

Essentially I reinstalled Ubuntu 9.10 (x64) onto a 500GB HD

/dev/sda1 mounted at / (10GB)
/dev/sda2 mounted at /home (10GB)
/dev/sda3 mounted at /backup (476GB)
/dev/sda4 swap (4GB)

When I delete files form /home, into the trash bin it goes :P

when I delete files from /backup, it tells me I cannot move it into trash, do I want to delete permanently? :(

How do I get trash to work on /backup (or any other non- /home directory)? :confused:

Thanks and :KS:KS:KS:KS:KS for everybody that can help.

ps. I really tried to search here and on google for the answer but no luck ;(

---

### Post by dcstar on 2009-12-17
> **bhsu17 said:**
> Hi peoples,

'lil help here please.

Essentially I reinstalled Ubuntu 9.10 (x64) onto a 500GB HD

/dev/sda1 mounted at / (10GB)
/dev/sda2 mounted at /home (10GB)
/dev/sda3 mounted at /backup (476GB)
/dev/sda4 swap (4GB)

When I delete files form /home, into the trash bin it goes :P

when I delete files from /backup, it tells me I cannot move it into trash, do I want to delete permanently? :(

How do I get trash to work on /backup (or any other non- /home directory)? :confused:


You use a Linux filesystem and not a rubbish filesystem like FAT.

---

