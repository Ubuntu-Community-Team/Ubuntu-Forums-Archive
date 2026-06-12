---
title: "Mysterious shell output"
date: 2010-09-09
forum: General Help
---

### Post by Ravenheart on 2010-09-09
I am running 10.04 and am trying to use the shell more.  I have come across a small problem.  I declare a variable **file="***"**.

I then type **echo $file** and instead of getting ******* as the output I get a listing of the files in my home directory!

Any help appreciated.

---

### Post by pbrane on 2010-09-09
It appears that what you are doing is the equivalent of **echo *** which will list all the files in the current directory.

```

file="***"
echo "$file"

```

quote **$file** when you echo it and you will get the results you want.

---

### Post by Ravenheart on 2010-09-09
Excellent.  Obvious when someone shows you how.

The expression **echo $file** evaluates as **echo ***** which I can verify gives you listing of the directory.

Much thanks, That's been bugging me for a few days.

---

