---
title: "empathy just keep connectiong to msn"
date: 2011-11-12
forum: General Help
---

### Post by OmerTatar on 2011-11-12
Hi all,

I am using Ubuntu 11.04 and using empathy for chating on googletalk and msn.To day I found out that empathy cannot connect to msn. It just showing connecting and never connects nor display any error. I cann connect to my msn from web so I didn't forget my password....any help

---

### Post by little.freaky on 2011-11-13
I've had the same problem. It started some days ago. Head over to [http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy](http://askubuntu.com/questions/76948/problems-connecting-msn-with-empathy) for a solution that worked for me.

have fun

---

### Post by OmerTatar on 2011-11-13
Thanks but it didn't work for me....:confused:

---

### Post by leawning on 2011-11-13
Hi, that method works for me, but I found that I was appearing offline on others' msn while I was online on my own machine. Any help?

---

### Post by OmerTatar on 2011-11-14
Solved!

Just edited:

/usr/share/pyshared/papyon/service/description/AB/__init__.py

changed line 23 to:

url = "http://local-sn.contacts.msn.com/abservice/abservice.asmx"

Killed empathy and started it again.

---

