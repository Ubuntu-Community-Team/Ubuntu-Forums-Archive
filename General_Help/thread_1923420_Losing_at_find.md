---
title: "Losing at find"
date: 2012-02-10
forum: General Help
---

### Post by hwttdz on 2012-02-10
I'm looking to create find command for two different lapack libraries I have installed on my machine, namely the blas and atlas versions of liblapack.a.  

I can find the atlas version by doing
```
find / -xdev -path "*atlas*" -type f -name "liblapack.a" 2>/dev/null
```

For the lapack version I'd like to say, "does not have atlas in the path", for which I attempted to use:
```
find / -xdev -path "*atlas*" -type f -name "liblapack.a" -prune -o -type f -name "liblapack.a" 2>/dev/null
```

But I get both.  Can someone point out my error?  Thanks.

Solution, find is being silly, and adding -print to the end of the -or half is sufficient to make it not show the others.  I was debugging by building it up piecewise, and apparently this is one of those cases where you need the whole thing for it to work.

---

