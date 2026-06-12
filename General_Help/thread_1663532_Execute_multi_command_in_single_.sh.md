---
title: "Execute multi command in single .sh"
date: 2011-01-09
forum: General Help
---

### Post by JCM_Pico on 2011-01-09
Hi there,
I've been trying to make a script to run a couple of executables that take a while to compute.
Example:
[I]
#!bin/bash
./cmd1.exe
./cmd2.exe[/I]

This tow commands are dependent of each other, first I need to run cmd1 and when it finish computing I should run cmd2.

But when I run my script it attempts to run it all at once....
Is there any way to make it wait for the cmd1 task to finish before running the next command?

---

### Post by JCM_Pico on 2011-01-10
any one?

---

### Post by sisco311 on 2011-01-10
Try:
```
#!bin/bash

./cmd1.exe
wait
./cmd2.exe
```

See:```
man wait
```

---

### Post by kaspar_silas on 2011-01-10
I think you want:
 
./cmd1.exe && ./cmd2.exe  

which means Run cmd1, then if cmd1 successful run cmd2.

However what you have should still run sequentially. Are you totally sure they are both trying to run at once and it's not just that the first fails then bash jumps to the second which also fails as the first did.

If you change to :

#!bin/bash
echo "STarting"
./cmd1.exe 
echo "Second Runs"
./cmd2.exe 

and run what do you get?

---

### Post by Grenage on 2011-01-10
Yes, the OP's example should definitely run sequentially.  I'd advice making doubly sure that they are actually running at the same time.

---

### Post by JCM_Pico on 2011-01-10
okidoki, problem solve
my example run sequentially as kaspar_silas said, I haven't change a thing...
I had an error in a variable path so it failed  to run the commands

thank you all for the help :D

---

