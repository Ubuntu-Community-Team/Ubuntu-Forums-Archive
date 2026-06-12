---
title: "convert cat output to html"
date: 2010-01-08
forum: General Help
---

### Post by michelkogan on 2010-01-08
Is there anyway to convert standard output to html ?

for example I wanna convert a colored file like this:

```
git diff -u --color-words --no-index ~/file1 ~/file2 > my_colorized_output
```

I wanna convert my_colorized_output ( or anything else ... ) to html format.

---

### Post by Lars Noodén on 2010-01-08
It depends on how the content could be processed to find a structure and mark it up.  

I'd imagine that you could use awk, but for sure [tidy](http://tidy.sourceforge.net/) will be of use.  It's in the Ubuntu repositories.  You can pipe data directly into tidy.

---

### Post by michelkogan on 2010-01-09
pipe data ? like this ???

```
my_colorized_file | tidy
```

---

### Post by Lars Noodén on 2010-01-09
> **michelkogan said:**
> pipe data ? like this ???

```
my_colorized_file | tidy
```

More like this:

```

git diff -u --color-words --no-index ~/file1 ~/file2 | tidy -asxml > my_colorized_output.html

```

Note that the example may not do anything useful beyond showing how to use a pipe.  

**>** sends output to a file

**<** reads input from a file

**|** sends output from one program as input to another

---

