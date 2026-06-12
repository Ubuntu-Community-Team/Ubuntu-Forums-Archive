---
title: "Command line FTP"
date: 2006-01-31
forum: General Help
---

### Post by SilverTab on 2006-01-31
I wanted to know if their are any parameters available for the "ls" command on a console ftp client??


My goal is to view the directory listing, sorted by date modified....however, regular ls parameters (-c etc..) arent working on a FTP.... from what I understand, the ls command, and the parameters, are sent to the ftp server... I tried several random attempts, nothing will work..

however, I can use pipe ( | ) to send the output in another program, so maybe there is a way to sort the output that way??

---

### Post by dcstar on 2006-02-01
[QUOTE=SilverTab]
......
however, I can use pipe ( | ) to send the output in another program, so maybe there is a way to sort the output that way??[/QUOTE]
Yes you can, pipe it to the inbuilt "sort" function ("man sort" will show you what you can do).

---

