---
title: "Rank in R. is it buggy or it just me?"
date: 2010-08-21
forum: General Help
---

### Post by castudil on 2010-08-21
Working in R, need the rank of some values (average). an found this weird behaviour. any explanation or it is a bug? I am using karmic 64 
Thanks

R version 2.9.2 (2009-08-24)
Copyright (C) 2009 The R Foundation for Statistical Computing
ISBN 3-900051-07-0


> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.33))
[1] 3 6 1 6 6 3 3
> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95))
[1] 3.5 6.0 1.0 6.0 6.0 3.5 2.0
> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.00))
[1] 3.5 6.0 1.0 6.0 6.0 3.5 2.0
> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.33))
[1] 3 6 1 6 6 3 3

---

### Post by kevin.krenz on 2010-08-22
Can you explain what you think the problem is? It looks like it's working to me.

---

### Post by castudil on 2010-08-22
Sorry I should be more explicit about what i was thinking :S

when I run

> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.33))
[1] 3 6 1 6 6 3 3

then I have a rank, where ties are solved as the min rank (like the ranks in sports)

now if I only take out the decimal part of the last number, like this

> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95))
[1] 3.5 6.0 1.0 6.0 6.0 3.5 2.0

the result now is a rank where ties are solved in 'average', and in 'min'.


same thing with:

> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.00))
[1] 3.5 6.0 1.0 6.0 6.0 3.5 2.0


I need rank that answers the average rank for the first case shown above,. i.e., rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.33)) ?

I already read the help for the Rank function, it says one should use the option 'average' but unfortunately I am still getting the same results shown above.

Thanks!

---

### Post by kevin.krenz on 2010-08-22
They're both averaging.

First example: 

> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95.33))
[1] 3 6 1 6 6 3 3

1. 92.67
2. 95.33
3. 95.33
4. 95.33
5. 96
6. 96
7. 96

Average of 2,3,4 is 3, average of 5,6,7 is 6.

Second example:

> rank(c(95.33,96.00,92.67,96.00,96.00,95.33,95))
[1] 3.5 6.0 1.0 6.0 6.0 3.5 2.0

1. 92.67
2. 95
3. 95.33
4. 95.33
5. 96.00
6. 96.00
7. 96.00

Average of 3,4 is 3.5, average of 5,6,7 is 6.0.

---

### Post by castudil on 2010-08-23
of course, you're right man!
sorry for the silly question and thanks a lot for your patience!

---

### Post by kevin.krenz on 2010-08-24
> **castudil said:**
> of course, you're right man!
sorry for the silly question and thanks a lot for your patience!

No problem, there's no such thing as a dumb question. Sometimes you just need someone else's perspective - I've done that plenty of times.

---

