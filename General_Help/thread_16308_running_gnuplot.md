---
title: "running gnuplot"
date: 2005-02-20
forum: General Help
---

### Post by Aurels on 2005-02-20
Hi.
I installed this 3 packages
- gnuplot
- gnuplot-nox
- gnuplot-x11

(version 4.0.0-2) 

I can run the program but I cannot plot anything...

when I use "plot x": no error but no graph...

Is there something special to do?

Thanks.

PS: when I statr gnuplot, I get the message terminal set to unknown

---

### Post by kassetra on 2005-02-20
Try typing:
  ```
set terminal postscript
``` 
 
 The problem is that you need to set what kind of output for gnuplot.
 
 "set terminal" tells gnuplot what to do with the output.
 
 you can also try:
 ```
set terminal x11
 set terminal png
 set terminal pdf
 set terminal svg
``` 
 
 Does that help?

---

### Post by WW on 2005-02-20
Aurels,

That's strange.  When I run gnuplot, after the introductory stuff is printed, I get
> Terminal type set to 'x11'
gnuplot>

As you can see, the default terminal type is 'x11'.  I don't know why yours would be unknown.  As kassetra suggested, you could try setting the terminal yourself
> set terminal x11
plot sin(x)


---

### Post by Aurels on 2005-02-21
I got an error when I do set term

```
gnuplot> set terminal x11
                      ^
         unknown or ambiguous terminal type; type just 'set terminal' for a list
``` 

x11 is not in the list when I do set term, that's strange because I've got the package gnuplot-x11 installed...

Thank you for the replies

---

### Post by Aurels on 2005-02-21
Problem found!

It was just my fault.  :-? 
I tried a month ago to compile gnuplot and I let some files at bad locations...

Thank you anyway!!!

 :-P

---

