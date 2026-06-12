---
title: "Need Help! How to copy files?"
date: 2011-07-08
forum: General Help
---

### Post by kelvin490 on 2011-07-08
I have to work in terminal but I don't know the command of copying files from one folder to another. 
 
e.g from /share/ParaDiS.v2.3.5.1 to /home/newfolder
 
what should I type?
 
Thank you

---

### Post by dasan on 2011-07-08
only one file or folder as it is

cp is the command to copy

cp /share/ParaDiS.v2.3.5.1/file name  /home/newfolder/filename

OR

cp -R /share/ParaDiS.v2.3.5.1  /home/newfolder

will also work i think

man cp for more about cp

---

### Post by kelvin490 on 2011-07-08
> **dasan said:**
> only one file or folder as it is
 
cp is the command to copy
 
cp /share/ParaDiS.v2.3.5.1/file name /home/newfolder/filename
 
OR
 
cp -R /share/ParaDiS.v2.3.5.1 /home/newfolder
 
will also work i think
 
man cp for more about cp
 
Very useful, Thanks man

---

### Post by NoFriends on 2011-07-08
cp /home/[COLOR=Red]**user**[/COLOR]/filename /home/user/**[COLOR=Red]newlocation[/COLOR]**/

or 

from different machines.

make sure your logged into the machine you want the file on.

scp user@lmachinename:/home/user/filename .

---

### Post by oldos2er on 2011-07-08
If you know what you want to do but are unsure of the exact command, use **apropos** ```
apropos copy
``` will spit out every type of "copy" command including the one you want (cp).

---

