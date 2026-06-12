---
title: "vim: problem with regex in substitution"
date: 2012-02-18
forum: General Help
---

### Post by dmikulec on 2012-02-18
Hi! 

I'm using vim 7.2. I've run into a problem with pattern matching. I have a text file which is running numbers together. They should be of the form n.nn nnnnn; but, instead, they are n.nnnnnnn. A search for the problem number with the pattern \([.]\d\d\)\(\d\{5}\) is successful. A replacement %s/\([.]\d\d\)\(\d\{5}\)\1 \2/g is not. I've tried reducing the repeats in the second word but the syntax just doesn't work for me.

Don

---

### Post by TeoBigusGeekus on 2012-02-18
> **dmikulec said:**
> %s/\([.]\d\d\)\(\d\{5}\)\1 \2/g

You've forgotten a slash between ) and \1.
This works for me:
```
%s/\(\.\d\{2}\)\(\d\{5}\)/\1 \2/g
```

---

### Post by dmikulec on 2012-02-19
Teo,

Thanks!

Don

---

### Post by TeoBigusGeekus on 2012-02-19
You're welcome Don.

---

### Post by Khayyam on 2012-02-19
or ... visual to !sed .. and have it insert a char (space) after the 4th.

:'<,'>!sed 's/./& /4'

Its shorter (particularly with "ctl-vG:") and alot less hassle than regex matching.

visual, I<space> would also work
 
HTH ..

---

