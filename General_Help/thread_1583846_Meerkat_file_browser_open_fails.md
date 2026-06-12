---
title: "Meerkat file browser open fails"
date: 2010-09-28
forum: General Help
---

### Post by hhoyt on 2010-09-28
I have a simple C program that runs fine in 10.04.
It fails in 10.10 (current maint) but I am baffled why the output file name is trashed.

I extract data from a file and then display it thru gedit.

If I run the c program, write out the modified file, and subsequently edit the output, all is well.

What I want to do is write out the modified file, and gedit it from my program. 
**What happens is that gedit cannot edit my file because its' name has been trashed. **
I read in file n4af0912.log, gather some data from it, and write it out to n4af0912.nsl, close the file, and attempt to gedit.
gedit comes up but in edit of n4af09p1a%0830 
mime type is plain text 
encoding utf8
gcc -o nsl nsl.c
i can do CLI './nsl n4af0912.log'
and he correctly writes out n4af0912.nsl
---
What I cannot do is select n4af0912.log from filelist and 'open with' other of './nsl'
gedit comes up with edit of garbage file (encl).
Something changed from 10.04, but I am not sure what ?
-----
The applicable C
fclose(fpo);  //close output
   strcpy(command, "gedit "); 
                       
                        strcat(command,ofile);
                        system(command); //gedit the file

Same failure off either nautilus or gnome-commander.

Thanks, Howard

---

### Post by hhoyt on 2010-10-03
solved. The problem was caused by not allocating enough space to a file open and had nothing to do with 10.10.

Howard

---

