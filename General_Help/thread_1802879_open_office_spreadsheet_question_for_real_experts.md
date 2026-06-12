---
title: "open office spreadsheet question for real experts"
date: 2011-07-12
forum: General Help
---

### Post by Acradon on 2011-07-12
Hello there, 

I am a little stuck right now. I am trying to put a relatively simple IF command into a cell. However, as usual there is a twist to the thing. IF the neighbouring cell shows "NO" than my cell shall calculate a result by multiplying two other cells...so far so good. I got that to work, However, NOW I would like the cell to show the result with a < (smaller than) in front of this multiplication result... Any ideas?

In short again: IF A=NO than B=<(C*D)

Thanks for your help in advance. And just to warn you guys ahead, there might be more of those questions in the future. 

Thank you

ACRADON

---

### Post by aytech on 2011-07-12
Do I get it right, you just want to have "<" sign in the cell plus the result?

---

### Post by Acradon on 2011-07-12
pretty much yes...

---

### Post by ugm6hr on 2011-07-12
Obviously, the "<" will make the cell text (rather than a calculation reslt).
I've not used concatenate with a calculation result before, but might be worth trying? i.e. calculate C*D, then add a < IF A<>NO
[http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Calc:_CONCATENATE_function](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Calc:_CONCATENATE_function)
[http://www.openofficetips.com/blog/archives/2005/02/text_manipulati.html](http://www.openofficetips.com/blog/archives/2005/02/text_manipulati.html)

---

### Post by aytech on 2011-07-12
Im not much experienced with Oo, but did you try to put the < sign in quotes? Like this: B="<"&" "&C*D (thats if you want it with the space).

//EDIT: too late:)

---

### Post by Acradon on 2011-07-12
That might work, however, if the A is not NO than it will be a number in which case B=A*D. So C only comes into play when A=NO

I know it is totally screwed....welcome to my life :)

---

### Post by Acradon on 2011-07-12
Thanks aytech, this works. I didn't know about the & symbol function. 

SOLVED

---

