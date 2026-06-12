---
title: "What file do I need to add programs to?"
date: 2010-08-08
forum: General Help
---

### Post by zozza on 2010-08-08
Hello,  

All programs are listed in a particular file so that you can type "thunderbird" rather than go to the specific directory and type ./thunderbird, for example. 

I cannot remember of find from Google what the file is?

Thanks.

---

### Post by oldos2er on 2010-08-08
It depends on how you installed Thunderbird; if you used a package manager, it's probably in /usr/bin (if that's what you're asking).

---

### Post by hwttdz on 2010-08-08
What your thinking of is actually your shell's path variable.  The shell searches directories in a specified order and runs the first one it comes across.  For instance I have a line 

export PATH=/home/user/bin:$PATH

in my .bashrc which adds my path to the path of the machine.  Anyways what you need is some variation on that 

export PATH=/path/to/tbird/:$PATH
setenv PATH (however it's done in tcsh)

You should be able to figure it out by looking at your .bashrc/.tcshrc/.zshrc ...

---

