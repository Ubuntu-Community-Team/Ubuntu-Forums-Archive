---
title: "move installed program?"
date: 2011-04-30
forum: General Help
---

### Post by bnhrobotics on 2011-04-30
I installed a few programs in my ~/Downloads folder. I would like to move them to /usr/local (I read this is where they belong). Is it as simple as copying and moving, or do I need to reinstall them in those locations?

---

### Post by 5149.5 on 2011-04-30
How were they installed? Are they just one file?

---

### Post by WorMzy on 2011-04-30
"Installing" something just means putting it in the right place, so you haven't "installed" them yet. You may have *compiled* them, in which case you can probably install by running
```
sudo make install
``` from the same directory you originally ran make from (assuming you used make, if you used a different tool, you may not have such an easy option)

---

### Post by bnhrobotics on 2011-04-30
It was multiple files and I used "make install".

---

### Post by hwttdz on 2011-04-30
When doing the configure you can usually do 
./configure --prefix=/usr/bin
make install will then require sudo permissions.  The INSTALL or README file in the package will usually cover how to do this.  It's also quite possible you can just move the binary, "sudo mv binary /usr/bin".

---

### Post by Lateralis on 2011-04-30
Alternatively, for programs that you compile yourself or are not part of the distro's repositories, you can create the directory ~/bin and place the program's binary file in there.  Or, the /opt directory can be used for such things.

---

### Post by bnhrobotics on 2011-04-30
So these files should go in /usr/bin rather than /usr/local?

---

### Post by oldos2er on 2011-04-30
If you use "sudo make install" as WorMzy suggests, it should place files in /usr/local/

---

### Post by bnhrobotics on 2011-05-01
I ended up using mv to put them into /usr/local. They work fine there. I'll mark this as solved. Thanks

---

