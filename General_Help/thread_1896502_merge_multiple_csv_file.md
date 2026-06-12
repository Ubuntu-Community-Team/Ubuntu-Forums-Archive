---
title: "merge multiple csv file"
date: 2011-12-17
forum: General Help
---

### Post by Marcello49 on 2011-12-17
Hi
I need help to solve the following problem: I have multiple (from 2 to 6) files. The first three columns identify a student the fourth is the results of an exam that can be taken more then once in different moments. They are of  the form

"MATRICOLA";"COGNOME";"NOME";"01_2012"
"5108932";"ABBATE";"LINO";"respinto"
"5129960";"ANTONELLI";"STEFANO";"Assente"
"5078925";"BONO";"GIULIA";"24/30"

They have different fourth columns

"MATRICOLA";"COGNOME";"NOME";"02_2012"
"5135682";"MARTI";"FRANCO";"Assente"
"5129960";"ANTONELLI";"STEFANO";"23/30"

 I would like to merge them in order to obtain

"MATRICOLA";"COGNOME";"NOME";"01_2012";"02_2012"
"5108932";"ABBATE";"LINO";"respinto"; " "
"5129960";"ANTONELLI";"STEFANO";"Assente"; "23/30"
"5078925";"BONO";"GIULIA";"24/30"; " "
"5135682";"MARTI";"FRANCO";" ";"Assente"

In other words a want to add the new column without duplicating the students.
Thanks for your help
Marcello

---

