---
title: "OpenOffice Spaces in Formulas"
date: 2009-10-16
forum: General Help
---

### Post by schnauzer93 on 2009-10-16
My work has me use a macro to generate price listings for buildings. When I do this, the formula it spits out is something like ```
=D12* E12
```

However, Calc does not like this and simply shows the formula in plain text, rather than what it evaluates to. Is there a way to make Calc automatically remove spaces from formulas so it looks more like this?

```
=D12*E12
```

EDIT: Spaces also show in Excel, but it does not have this problem.

---

### Post by Mariane on 2009-10-16
I would suggest trying with the automatic find and replace functions (in the functions which corrects usual typos) if you can set it to selectively replace what you want (eg "* " by "*" and not just " " by ""). 

The precise way would depend on the version of OO you are using and it doesn't always work. In one version of OO I never managed to stop it from replacing "5 %" by "5%" even though I tried for quite a while. 

The problem is easy is you tell it it is all text, but you don't want to do that or it won't do the calculations. 

Mariane

---

