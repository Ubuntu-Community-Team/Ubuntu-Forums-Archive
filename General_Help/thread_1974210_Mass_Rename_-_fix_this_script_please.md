---
title: "Mass Rename - fix this script please"
date: 2012-05-05
forum: General Help
---

### Post by minigilani on 2012-05-05
Hi

Could someone help me with a mass rename? I need to replace brackets with nothing. And i have zero experience with scripts. I found one and kind of edited it, but i cannot get it to work right. Here:

For the left bracket:
```
> for i in *;
> do x=$( echo $i | grep '(' | sed 's/(/\/g' );
> if [ -n "$x" ];
> then mv $i $x;
> fi;
> done;
```

For the right bracket:
```
> for i in *.html;
> do x=$( echo $i | grep ')' | sed 's/)/\-/g' );
> if [ -n "$x" ];
> then mv $i $x;
> fi;
> done;
```

Thanks!

---

### Post by papibe on 2012-05-05
Hi minigilani.

You can use 'rename' and solve that very easily with a couple of runs:
```
rename 's/\(//g' *

rename 's/\)//g' *
```
Hope that helps.
Regards.

---

### Post by sisco311 on 2012-05-05
+1 for the Perl based rename:
```
prename -n 's/[()]//g' ./*
```

I'm too lazy right now to write shell script equivalent. :)

---

### Post by minigilani on 2012-05-05
> **papibe said:**
> Hi minigilani.

You can use 'rename' and solve that very easily with a couple of runs:
```
rename 's/\(//g' *

rename 's/\)//g' *
```


Haha! Thanks! Worked perfectly!

> **sisco311 said:**
> I'm too lazy right now to write shell script equivalent. :)

Lol, i know that feeling! :p

---

