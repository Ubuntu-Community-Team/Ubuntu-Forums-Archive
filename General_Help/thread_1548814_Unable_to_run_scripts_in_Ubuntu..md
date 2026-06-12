---
title: "Unable to run scripts in Ubuntu."
date: 2010-08-08
forum: General Help
---

### Post by positronium on 2010-08-08
I'm trying to run a script to make compiling fortran programs easier.
I have placed the script in directory: /usr/bin/

I have tried placing the same script file in directories with no success: /bin and /home/myself/bin

I have also added myself to the root user group.

here is my terminal window: (the script is fortfit and the 
myself@mycomputer:~/prog$ fortfit velo
bash: /usr/bin/fortfit: Permission denied

and I also tried:
myself@mycomputer:~/prog$ sudo fortfit velo
sudo: fortfit: command not found

I have the same script working like it should on an Apple (but that computer belongs to my University).  
Does anyone have any ideas for me?  Is there a bin folder that the terminal will look in that I don't need some crazy permissions for?
Thank you.

---

### Post by CharlesA on 2010-08-08
Does it have execute permission?

---

### Post by positronium on 2010-08-09
That was it!  
Thank you CharlesA!

---

