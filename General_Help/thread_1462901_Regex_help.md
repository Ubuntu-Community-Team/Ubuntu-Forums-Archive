---
title: "Regex help"
date: 2010-04-26
forum: General Help
---

### Post by CatchItBaby on 2010-04-26
I have some textfile and i want to rename

backup_myfile.txt should be myfile.txt
wolf**backup**tiger_backup_theory.txt should be wolfbackuptiger_theory.txt

but in above case it generate output like this wolftiger_theory.txt

Regex i m using

[._-]?(back|backup)[._-]?

Can anyone Help me..

---

### Post by CatchItBaby on 2010-04-26
any one ?

---

### Post by CatchItBaby on 2010-05-02
Any one ?

---

### Post by rnerwein on 2010-05-02
hi
try this:
rename 's/backup_//'  backup_myfile.txt   results in  --> myfile.txt
rename 's/backup_//'  wolfbackuptiger_backup_theory.txt results in --> wolfbackuptiger_theory.txt

for i in `ls *.txt`
do
rename 's/backup_//' $i
done

other files ending with *.txt and ain't include "backup_" are not touched.

have fun
ciao

---

