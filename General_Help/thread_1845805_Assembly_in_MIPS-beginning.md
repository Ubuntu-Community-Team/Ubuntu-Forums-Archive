---
title: "Assembly in MIPS-beginning"
date: 2011-09-17
forum: General Help
---

### Post by jason.hunsaker on 2011-09-17
I recently started learning assembly in my CS 3810 course. I'm using QtSpim and am very new to this. This is my assignment: 

"Write a MIPS program that allows a user to enter two numbers and then an  operation.  The program should display the result.  The only operations  that you must include are addition and subtraction.  The program should  continue until the user indicates that they are done.  In addition to  these requirements your program must include at least one function call  (jal instruction) and one loop construct (the equivalent of a for or  while loop)."

I have most of it written. The only problem I'm encountering is when it comes to the user choosing which operation to perform on the numbers entered(+ or -). Once the user enters the operand, how do i determine whether i take the user-entered numbers and branch to an addition label or a subtraction label? I need some way of comparing the user-entered operand with the + and - signs. 

Any code, hints, or explanations will be helpful. Thanks!

Jason

---

### Post by jason.hunsaker on 2011-09-17
I recently started learning assembly in my CS 3810 course. I'm using QtSpim and am very new to this. This is my assignment: 

"Write a MIPS program that allows a user to enter two numbers and then an  operation.  The program should display the result.  The only operations  that you must include are addition and subtraction.  The program should  continue until the user indicates that they are done.  In addition to  these requirements your program must include at least one function call  (jal instruction) and one loop construct (the equivalent of a for or  while loop)."

I have most of it written. The only problem I'm encountering is when it  comes to the user choosing which operation to perform on the numbers  entered(+ or -). Once the user enters the operand, how do i determine  whether i take the user-entered numbers and branch to an addition label  or a subtraction label? I need some way of comparing the user-entered  operand with the + and - signs. 

Any code, hints, or explanations will be helpful. Thanks!

Jason

---

### Post by jason.hunsaker on 2011-09-17
I recently started learning assembly in my CS 3810 course. I'm using QtSpim and am very new to this. This is my assignment: 

"Write a MIPS program that allows a user to enter two numbers and then an  operation.  The program should display the result.  The only operations  that you must include are addition and subtraction.  The program should  continue until the user indicates that they are done.  In addition to  these requirements your program must include at least one function call  (jal instruction) and one loop construct (the equivalent of a for or  while loop)."

I have most of it written. The only problem I'm encountering is when it  comes to the user choosing which operation to perform on the numbers  entered(+ or -). Once the user enters the operand, how do i determine  whether i take the user-entered numbers and branch to an addition label  or a subtraction label? I need some way of comparing the user-entered  operand with the + and - signs. 

Any code, hints, or explanations will be helpful. Thanks!

Jason

---

### Post by anewguy on 2011-09-17
Should be a fairly straight forward compare with a branch or branch and link for each operation - if the assembler supports a "case" statement (not the usual case for assembler) you could do it that way as well.

Can't give you any more specifics because then we would be doing your assignment for you, eh?  ;)

Dave ;)

---

### Post by overdrank on 2011-09-17
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

