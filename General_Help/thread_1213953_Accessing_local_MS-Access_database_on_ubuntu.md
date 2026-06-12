---
title: "Accessing local MS-Access database on ubuntu ?"
date: 2009-07-15
forum: General Help
---

### Post by Bob Unitt on 2009-07-15
Gentlefolk,

I'm trying to open a local MS Access database via ODBC on a ubuntu (8.04) system. I've got MySQL working via ODBC, so I know the basics of ODBC are installed and functional, but I don't know how to apply them to an MS Access db which sits on the same ubuntu box.

I've searched the forums and google for information on this, but I've just got more and more confused by what I've found...

In order to access a local MySQL file via ODBC, I have to have the various MySQL Database Server services running, and I have to have an 'ODBC Driver' entry for the driver software and a 'User DSN' entry for the database itself.

What I can't discover is what the equivalents are for MS Access :-

1) What Unix service must I run to provide the Access Database Server function ?

2) What are the Access 'ODBC Driver' equivalents of 'libmyodbc.so' and ' libodbcmyS.so' ?

3) What 'Keyword'/'Value' pairs do I need in the 'User DSN' entry.
  
4) Is what I'm trying to do actually possible under ubuntu 8.04 ?

BTW - I know there are better ways of holding and accessing data than MS Access on Linux, but I'm trying to perform an exercise from a tutorial book, so please only address the questions asked, rather than "you don't want to do it that way" (UK in-joke for those of a certain age)...

TIA
-- 
Bob Unitt

---

