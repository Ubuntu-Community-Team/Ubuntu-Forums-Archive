---
title: "MU server on Ubuntu Server with Wine - Works?"
date: 2009-09-15
forum: General Help
---

### Post by kristapsb on 2009-09-15
Hello,

I want to create my own MU Online server. I am using Ubuntu Server. Will MU Online server run on this system with Wine? Has anybody done something like this?

Thanks
kristapsb

---

### Post by Andertraaks on 2009-09-15
Well, I've worked with Private Servers on my own, but not MU. But if you can get your database and server get to work together, I think it's possible. 

In RuneScape, I had to correct the way the java files got information from item lists etc, by correcting to path's to folders, example(I guess you're not emulating the server files, if they are, you might aswell ignore this): 
Original: \\source\\lists\\items.cfg 
On Linux: /source/lists/items.cfg
I hope you understood what I was trying to explain, I find it hard to get people to understand things that I try to explain.

Regards,
Andertraaks.

---

### Post by kristapsb on 2009-09-15
Thanks. Oh, I just found out that Mu uses Mssql insteat of Mysql, which means I need to modify all database queries. Seems a bit too hard for me :(

---

