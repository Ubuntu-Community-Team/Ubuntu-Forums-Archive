---
title: "Modify .bashrc"
date: 2010-01-12
forum: General Help
---

### Post by Diametric on 2010-01-12
So, I'd like to permanently change my $PATH.  I know I need to edit my .bashrc file with the following code:

```
PATH=$PATH:/home/myusername/bin
export PATH  

```
But, my question is, where is this placed in the .bashrc?  Once I get that saved I'll

```
source ~/.bashrc
```

---

### Post by cong06 on 2010-01-12
I had to just add it to mine:

```

PATH=$PATH:/home/user/docs/scripts

```

I put it around line 16, after the first two exports.

I'm sure you can mess around with it and figure out where to put it, since I doubt it matters much.

---

### Post by balmar on 2010-01-12
I have my ~/bin in the path automagically, without anything needed in .bashrc. Otherwise I don't think it matters much where to put path in .bashrc.

---

### Post by Diametric on 2010-01-12
Ok, just added the line after .bashrc sets the PS1 (around line 60 or so) variable and it worked great!  My first time modifying a script...I got the eye of the tiger, it's the thrill of the fight!

Thanks for the help.

---

