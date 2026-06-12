---
title: "about using openstat"
date: 2011-08-06
forum: General Help
---

### Post by chirag9 on 2011-08-06
hello..
Im using openstat for muliple regression analysis..
I want to know the least numbers of observations required to get the result window..
thanks

---

### Post by SeijiSensei on 2011-08-06
I don't know about openstat, but the answer to your question in general is that there needs to be more observations than independent variables.  If the number of independent variables is identically equal to the number of observations, regression is equivalent to solving a system of N equations in N unknowns.  As N increases relative to k, the number of predictors, you get a more "statistical" solution.  If N<k it's not possible to compute estimates for the regression coefficients.

BTW, if you're looking for a very powerful open-source regression package, I heartily recommend [gretl]("http://gretl.sourceforge.net/").  It's in the Ubuntu repositories.

---

### Post by chirag9 on 2011-08-17
thanx man..!!

---

