---
title: "Help with a basic loop in Stata (ver 11)"
date: 2011-04-15
forum: General Help
---

### Post by Megg22 on 2011-04-15
Hi,
 
Im new to Stata and am having trouble running a loop. I want to reg one variable on another, subject to fund no.
Fund no is a variable name with values from 1 to 357.
So basically I want to repeat the same regression (reg equity return) 357 times without having to do 
reg equity return if fundno ==1
reg equity return if fundno ==2
etc
 
So I tried 
foreach var of varlist fundno {reg equity return}
 
I know its something simple but I cant figure it out! 
Also, is there anyway of storing all the output? The output window only displays a certain amount of results and 357 will be too much and Ill miss out of some of the results. 
 
Thanks a lot!

---

