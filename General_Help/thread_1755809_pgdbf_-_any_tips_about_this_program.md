---
title: "pgdbf - any tips about this program?"
date: 2011-05-11
forum: General Help
---

### Post by Roger49 on 2011-05-11
[SIZE=2]Hi all,
I'm [/SIZE][SIZE=1][SIZE=2]exploring Ubuntu as a possible upgrade path for the future from Windows.
I have a small research database, originally created in Foxpro, which includes a Memo field. I would like to transfer this to my Ubuntu installation. OO Base will open the .dbf file, but not the .fpt file, which contains important info (well to me anyway...) I've found and installed pgdbf through Synaptic, and realise that I will also need to install an SDBC driver in order for OO Base to interact with a postgresql db engine.
My question is; I've "pgdbf'd" the files in question, and it seems to just echo the data in the table to the Terminal window. I can't seem to find a file that has been produced. Am I missing something?
I would be grateful for any tips on this.
All the best,
Roger49[/SIZE]

[/SIZE]

---

### Post by Roger49 on 2011-06-05
Hi All,
Further to my first post, there is success!
Installing the sdbc driver seemed to automatically ?install and start a postgresql 8.4 server.
This gave me the postgresql option in OO Base.
I spoke to a passing guru at work, and was told about sending output to a file using the ">" symbol.
I obtained a Postgresql book at a very good price, at  *m*z*n M*rk*tpl*c*, and read a little.
What I needed to do was similar to loading saved data back into a database after a "Dump" command.
The OpenOffice Wiki supplied the instructions on "Connecting to a Postgresql Database"
I have just opened my simple single-table database, with it's memo field in OO Base,
and created a Form. Job Done!!:P

---

