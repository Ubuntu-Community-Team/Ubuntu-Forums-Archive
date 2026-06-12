---
title: "Ubuntu's calculator not working!!!"
date: 2010-03-19
forum: General Help
---

### Post by ram2500 on 2010-03-19
I am reviewing trigonometry with my I.S. students as part of the Triangular Physics project that I have assigned, and I have brought my own laptop (with Ubuntu) to work with me. However, I am having deep troubles using Ubuntu's calculator with parentheses. For example, even a simple equation such as this

**2(3^5 - 6^4)**

...brings a "Malformed Expression" message. I know that I'm doing nothing wrong, but why can't Ubuntu's (Gnome) calculator handle parentheses?

---

### Post by Onesimus on 2010-03-19
Don't you have to put a '*' after the 2

---

### Post by ram2500 on 2010-03-19
I suppose I can use my scientific calculators (they are TI-89's and they, like most calculators, do not require the multiply symbol between a number and the parentheses to multiply the parenthetical contents. But, I cannot show my TI-89's output like I can with my computer!

The equation I typed in above, is an example, and not my real equation. 

I suppose, after all, I would just have to have students carefully listen and input the equation and see for themselves, if there is no fix.

---

### Post by ram2500 on 2010-03-19
I gave placing the multiply sign trick a try (I had my doubts) and it worked!:)

I'll keep this in mind, and thank you!

---

### Post by Onesimus on 2010-03-19
I find that if I type:

2x(3^5 - 6^4)

into the calculator then it is not a malformed expression.  When writing out the equation on paper and the multiply symbol is missed out, this is merely shorthand.  I find no problem with the fact that the multiply symbol needs to be there.

Presumably you would have no problem with 

2/(3^5 - 6^4)

to represent division ?

---

### Post by timgood on 2010-03-19
Have you tried installing:

Galculator

 
galculator is a scientific calculator. It supports different number bases (DEC/HEX/OCT/BIN) and angles bases (DEG/RAD/GRAD) and features a wide range of mathematical (basic arithmetic operations, trigonometric functions, etc) and other useful functions (memory, etc) at the moment. galculator can be used in algebraic mode as well as in Reverse Polish Notation.

You can install it from Ubuntu Software Centre. Hope this helps.

---

### Post by ubuntu27 on 2010-03-19
Hi ram2500.

I recommend you to install [Qalculate]("http://qalculate.sourceforge.net/").

I believe it to be the best GUI calculator. It supports paranthesis, it has unit conversion, log, in. It can also add variables and many more.

It is in the Ubuntu's repository so you can install with Synaptic P.M or by the Terminal:


```
sudo apt-get install qalculate
```

---

