---
title: "bash script for interacting with gromacs"
date: 2012-02-03
forum: General Help
---

### Post by fra11 on 2012-02-03
Hi!
I have to use the gromacs command trjconv to obtain a .gro file from a  .xtc and a .pdb file. I have to do it for several files in a bash for  loop so I'd rather prefer to find a way to make my script type in the  trjconv interactive terminal always the same number for the system. Any  tips?
Thanks
Fra

---

### Post by amauk on 2012-02-03
> **fra11 said:**
> Hi!
I have to use the gromacs command trjconv to obtain a .gro file from a  .xtc and a .pdb file. I have to do it for several files in a bash for  loop so I'd rather prefer to find a way to make my script type in the  trjconv interactive terminal always the same number for the system. Any  tips?
Thanks
Fra
Don't know what gromacs is, or what it does
but it sounds like it's an interactive CLI program similar to the FTP or MySQL CLI programs
If so, you should be able to feed it an arbitrary list of commands - Have a play around and see if it works

Just some examples of automation from the FTP and MySQL interactive CLI

```
ftp -inv ftp.example.com<<ENDFTP
user bob pa55w0rd
cd /htdocs/foo
lcd /mnt/bar
put baz.txt
bye
ENDFTP
```

```
mysql db_name < input.sql > output.txt
```

---

### Post by fra11 on 2012-02-03
well...apparently it doesn't work...
my script is like 
```

#!/bin/bash
trjconv -f md_test.xtc -s ../prova6/dynamin_dimer_phfitted.pdb -o tentativo.gro

```
and then it opens an interactive window where I just have to type 0
any help???
:confused:

---

### Post by amauk on 2012-02-03
What is this '0' you have to type in?
is it some extra variable that the program needs?

You could try just piping a '0' in, see if that works
```

#!/bin/bash
echo "0" | trjconv -f md_test.xtc -s ../prova6/dynamin_dimer_phfitted.pdb -o tentativo.gro

```

---

### Post by fra11 on 2012-02-03
It works.
Thank you!!!
:KS

---

### Post by amauk on 2012-02-03
no problem

Though, just be comfortable in your own mind exactly what that '0' is doing

Will it always be a '0'
or is there a case where it needs to be a different number

---

