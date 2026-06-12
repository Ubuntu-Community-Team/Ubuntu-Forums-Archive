---
title: "Comparing two files."
date: 2011-07-03
forum: General Help
---

### Post by Reddoug on 2011-07-03
Hi 
I am comparing two files using cmp, cmp -b and cmp -l.

Dxxx_Descendant_Report.odt Dean_Descendant_Report2.odt differ: byte 11, line 1 is  42 " 100 @ 

Dxxx_Descendant_Report.odt Dean_Descendant_Report2.odt differ: byte 11, line 1 
To me it looks like a problem with line 1 but I do not see any difference.
cmp -l gives a whole lot of numbers.

Thanks, Doug

---

### Post by Habitual on 2011-07-03
an alternative:

```
md5sum Dxxx_Descendant_Report.odt Dean_Descendant_Report2.odt
```

If they are identical, their hashes will be too.

---

### Post by psusi on 2011-07-03
What do you mean you don't see any difference?  .odt is a binary file, so it makes no sense to talk about lines and compare them.

---

### Post by Reddoug on 2011-07-03
Hi 
I used the cmp -i -b switches and this is what it returned;
Dxxx_Descendant_Report.odt Dean_Descendant_Report2.odt differ: byte 11, line 1 is 42 " 100 @

Dxxx_Descendant_Report.odt Dean_Descendant_Report2.odt differ: byte 11, line 1 

The .odt is what Lebre Office saved the files as. I am trying to figure out what  "byte 11, line 1 is 42 " 100 @" is telling me. I I look at the files side by side I do not see any differences. Just trying to learn something.

Doug

---

### Post by AlphaLexman on 2011-07-03
It is probably just a file modification difference. OOo keeps internal creation and modified times separate from bash's stat's.

I opened an existing *.odt file, saved it as a copy, then did a '**cmp**' against the two files, and got the same error.

---

### Post by Reddoug on 2011-07-03
Thank you. I did not give that a thought.

Doug

---

